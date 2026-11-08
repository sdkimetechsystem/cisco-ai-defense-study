## Antares CLI 가이드

### 1. Antares ClI 설치
* 환경 준비
  - sudo apt install -y ripgrep tree
  - curl -LsSf https://astral.sh/uv/install.sh | sh
  - source ~/.bashrc
* Antares 설치
  - uv tool install cisco-antares-cli </br>
    <img width="607" height="127" alt="image" src="https://github.com/user-attachments/assets/713dbd14-1034-41a9-b197-846b8000639a" />
  - antares --help </br>
    <img width="615" height="356" alt="image" src="https://github.com/user-attachments/assets/e0b8bd25-603e-49b7-8cf1-e8594a37943c" />

### 2. Antares 환경변수 파일 만들기 </br>
  - mkdir -p ~/.antares
  - nano ~/.antares/profiles.toml </br>
    [profiles.local-llama] </br>
    display_name = "Local llama.cpp" </br>
    model = "antares-350m" </br>
    backend = "remote" </br>
    endpoint = "http://127.0.0.1:8080/v1/completions" </br>
    context_window = 16384 </br>
    remote_timeout_seconds = 1800 </br>

    [profiles.local-llama.generation] </br>
    max_tokens = 1024 </br>
    temperature = 0.3,</br>
    top_p = 1.0 </br>
    frequency_penalty = 0.3,</br>
    stop_tokens = ["<|end_of_text|>", "<|start_of_role|>"]  </br>
    use_completions_api = true  </br>

### 3. antares 모델 설정 확인
 - antares models list </br>
   <img width="608" height="143" alt="image" src="https://github.com/user-attachments/assets/286f89a9-9ca1-4659-a0f5-e3719e092218" />

### 4. 테스트
 - 테스트 파일 만들기
   - mkdir -p ~/testrepo && cd ~/testrepo </br>
     cat > app.py <<'EOF'v
     import sqlite3</br>
      from flask import Flask, request </br>
     app = Flask(__name__) </br>
     @app.route("/user") </br>
     def user(): </br>
    name = request.args.get("name") </br>
    conn = sqlite3.connect("db.sqlite") </br>
    cur = conn.execute("SELECT * FROM users WHERE name = '" + name + "'") </br>
    return str(cur.fetchall()) </br>
    EOF </br>
 - 테스트 실행
   - antares plan ~/testrepo --max-cwes 3
     <img width="718" height="353" alt="image" src="https://github.com/user-attachments/assets/b3954d0a-01e2-4d0d-92cd-b22cab1c90ba" /> 
   - antares query ~/testrepo --cwe CWE-89 --profile local-llama --tool-budget 5
   
