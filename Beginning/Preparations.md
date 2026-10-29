# Cisco AI Defense를 준비하기 위해서는 가장 먼저 Cisco Black Belt Academy에서 기본 지식을 학습한다.

## 간단메모 : [ 2026-10-23 Cisco AI 시대 사이버 보안 워크숖 ]
### 1. Discovery of AI Agents  (D-cloud에서 확인 가능)
- Cisco Cloud Control > Agentic Security
- Secure Access : Agent gateway..모든 사용자&Agent traffic monitoring을 통한 Discocvery
- MCP&Tool Governance : User <-> MCP Client <-> Agent <-> Agentic Gateway <-> MCP Server <-> RAG, Web Search, SaaS APIs
- AI Agent 액션 차단, privacy protection
### 2. AI Defense (Cisco Cloud Control로 management, 별도 제품)
  - AI Red teaming 기능
  - Runtime 보호 : API 방식 / Gateway 방식 모두 지원 (GencoreAI, Lakera는 API 방식), PII/PCI/PHI 지원
  - [중요] Hybrid deployment에서 On-premise에 Detector 배포시 GPU 서버 필요
  - <img width="400" height="350" alt="image" src="https://github.com/user-attachments/assets/9226e779-525f-48b9-be88-fff0e42dcf63" />

### 3. Agentic gateway (Part of Secure Access, 별도 SKU 없음)
### 4. Cisco 오픈소스
  - FSS
  - CodeGuard
  - Isovalent
  - Antares
  - DefenseClaw (Enterprise 버전은 Secure Client + DefenseClaw)
  - IDE AI Security Scanner
  - Token Meter (By Splunk, 토큰 사용량 모니터링 on my laptop)

[ MITRE AI Maturity Model ]
<img width="1211" height="483" alt="image" src="https://github.com/user-attachments/assets/176b0e3e-2802-43e0-82df-ad8e7157eb29" />

1. Cisco Black Belt Academy (AI-Ready Infrastructure)
   URL - https://partnerlearning.cisco.com/new/ui/learner/page/1886901473278727616

2. 추천 이수 과목
   - AI Fundamentals (Stage 1, Stage 2)

4. 
