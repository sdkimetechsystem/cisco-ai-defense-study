## Antares 구동 테스트
### 1. Virtual box 설치
### 2. Virtual box에 Ubuntu OS 설치 
* VM의 Network 설정을 "어댑터에 브리지"로 설정 
* ip route 명령으로 route table 확인, 외부 ping 확인 
* 패키지 설치 및 준비 
  - sudo apt update && sudo apt install -y python3-venv python3-dev build-essential git curl 
  - python3 -m venv ~/vllm-env 
  - source ~/vllm-env/bin/activate 
  - pip install -U pip

### 3. Huggingface에서 Antares 모델 검색 (fdtn-ai/antares-350m)
* Access 요청
* 권한 완료 </br>
  <img width="507" height="40" alt="image" src="https://github.com/user-attachments/assets/6bd4dac3-2fe6-4e14-90fd-ee9c817b7f5a" />
* 계정 > Access Token > +Create New Token and save token ("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")

## 4. llama.cpp 설치 
* git clone https://github.com/ggml-org/llama.cpp
    <img width="778" height="112" alt="image" src="https://github.com/user-attachments/assets/065135ae-b0ad-44bc-9975-ff05f849429e" />
* cd llama.cpp
* sudo apt install cmake
* sudo apt install -y build-essential cmake git
* cmake -B build
* cmake --build build -j --target llama-cli llama-server llama-quantize
* 위 명령어의 부하를 줄이려면..양자화는 선택..
  - cmake --build build -j 1 --target llama-cli llama-server

## 5. HF에서 Model 다운로드
* HF에 로그인
#### ** vm 환경에서 설치시 externally관련 오류 발생할 수 있음.. 아래 방법으로 실행
  - sudo apt install -y python3-venv python3-pip
  - python3 -m venv ~/venv
  - source ~/venv/bin/activate
  - pip install -U "huggingface_hub[cli]"
* 계속 수행
  - pip install -U "huggingface_hub[cli]"
  - hf auth login        # 화살표 내려서 token으로 로그인 선택해서 토큰 paste
* Model 다운로드
  - hf download fdtn-ai/antares-350m --local-dir ./antares-350m
* GGUF로 변환
  - cd llama.cpp
  - pip install -r requirements.txt
  - python convert_hf_to_gguf.py ../antares-350m --outfile ../antares-350m-f16.gguf --outtype f16
    <img width="776" height="492" alt="image" src="https://github.com/user-attachments/assets/07ae25bb-2455-4522-a821-ea5101e68457" /> </br>
    - command 'python' not found 일 경우, 아래 명령 실행
      - source ~/venv/bin/activate
      - python --version
    - ModuleNotFoundError: No module named 'torch' 오류 발생할 경우
      - source ~/venv/bin/activate
      - pip install torch --index-url https://download.pytorch.org/whl/cpu
    - ModuleNotFoundError: No module named 'numpy' 오류 발생할 경우
      - pip install numpy
    - torch, numpy 설치 확인 방법
      - python -c "import torch, numpy; print('ok')"
    - 계속 설치 오류발생할 경우 하나씩 수동 설치
      - pip install --no-cache-dir numpy
      - pip install --no-cache-dir protobuf
      - pip install --no-cache-dir safetensors
      - pip install --no-cache-dir sentencepiece
      - pip install --no-cache-dir gguf
      - pip install --no-cache-dir transformers
 
## (Option) 양자화
* ./build/bin/llama-quantize ../antares-350m-f16.gguf ../antares-350m-q8_0.gguf Q8_0

## 6. 실행
* ./build/bin/llama-server -m ../antares-350m-q8_0.gguf -c 8192 -t 4 --host 127.0.0.1 --port 8080 --jinja

## 7. 동작확인
* curl http://localhost:8080/v1/chat/completions -H "Content-Type: application/json" -d '{"messages":[{"role":"user","content":"Hello"}],"temperature":0.2}'
