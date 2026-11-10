## Cisco CodeGuard MCP Server 설치
<img width="468" height="101" alt="image" src="https://github.com/user-attachments/assets/44f5456e-a800-4e07-8cbc-a6369672870e" />

### 1. 필수 패키지 설치
- sudo apt update
- sudo apt install nodejs npm
- nodejs -v, npm -v

### 2. MCP-Server 설치
- mkdir ~/codeguard-mcp && cd ~/codeguard-mcp
- npm install @isagasi/codeguard-mcp-server
- npx @modelcontextprotocol/inspector node ~/codeguard-mcp/node_modules/@isagasi/codeguard-mcp-server/dist/index.js 
