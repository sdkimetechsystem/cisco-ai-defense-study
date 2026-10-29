### 
### 1. Diagram
#### - AI Gateway Pattern
<img width="400" height="400" alt="image" src="https://github.com/user-attachments/assets/dd430fce-8312-43e3-8b6c-aed572a2c383" />

#### - Chat Application
<img width="640" height="500" alt="image" src="https://github.com/user-attachments/assets/d063a2cc-c873-401d-9f8b-4cffb456e174" />

#### - Document Processing Pattern
<img width="600" height="800" alt="image" src="https://github.com/user-attachments/assets/f296f8cd-2ec4-4c06-adf4-5707e9c458da" />

#### - Agent and Workflow Pattern
<img width="800" height="550" alt="image" src="https://github.com/user-attachments/assets/7b39eac3-59bc-4467-bd66-7bcddb14902b" />

### 2. Self-hosted requirements
GPU servers are supported and recommended for certain components of the self-hosted AI Guardrails deployment, but they are not required for all components.

GPU Support in Self-Hosted Deployments
The self-hosted deployment includes GPU-accelerated components 

Triton Inference Server – GPU-accelerated inference for text classifiers
Triton TensorRT-LLM – GPU-accelerated inference for Audio Defense
GPU support was added for self-hosted containers with compatibility for any CUDA 12.x GPU, which accelerates request processing
