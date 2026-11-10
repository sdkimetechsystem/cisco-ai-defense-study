## Cisco CodeGuard MCP Server 설치
<img width="468" height="101" alt="image" src="https://github.com/user-attachments/assets/44f5456e-a800-4e07-8cbc-a6369672870e" /> </br>
[참고] Virtualbox VM 간 내부 네트워크 연결을 위해서는 "NAT 네트워크" 모드로 설정

### 1. 필수 패키지 설치
- sudo apt update
- sudo apt install nodejs npm
- nodejs -v, npm -v

### 2. MCP-Server 설치
- mkdir ~/codeguard-mcp && cd ~/codeguard-mcp
- npm install @isagasi/codeguard-mcp-server
- npx @modelcontextprotocol/inspector node ~/codeguard-mcp/node_modules/@isagasi/codeguard-mcp-server/dist/index.js 
&nbsp; &nbsp;<img width="786" height="320" alt="image" src="https://github.com/user-attachments/assets/e6cb5e60-ddb5-4427-aa96-8357535cb284" />

- 브라우저가 자동 실행되고, codeguard-server GUI로 자동접속됨 (Connected로 토글 이동)
&nbsp; &nbsp;<img width="1729" height="839" alt="image" src="https://github.com/user-attachments/assets/5114d8f6-ca6c-4883-a8ef-d4c7be936c1d" />

- Codeguard Web UI는 6274 port(http://127.0.0.1:6274) 이지만, 외부 API port는 6275 임

### 3. MCP-Server 동작 확인
- Tools tab
&nbsp; &nbsp;<img width="899" height="351" alt="image" src="https://github.com/user-attachments/assets/0a286070-4251-4c73-8d14-e37644e3578e" />

- Tools 동작 검증
  - import hashlib </br>
    def save(pw): return hashlib.md5(pw.encode()).hexdigest()  </br>
    query = "SELECT * FROM users WHERE id=" + user_id  </br>
  <img width="540" height="305" alt="image" src="https://github.com/user-attachments/assets/e4e127ac-6940-4950-9f60-2b318fc5776f" />
  <img width="540" height="500" alt="image" src="https://github.com/user-attachments/assets/2d69e882-ce42-420e-9c54-87ca4f07d785" />

