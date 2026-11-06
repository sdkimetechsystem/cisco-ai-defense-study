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

