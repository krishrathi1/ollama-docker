Here’s a well-structured GitHub description for running **Ollama** on **Docker**, incorporating all the provided details:  

---

# 🐳 Ollama Docker Image  

Ollama makes it easy to run **large language models (LLMs) locally** using **Docker**. This setup supports **CPU, NVIDIA GPU, and AMD GPU** configurations for optimal performance.  

🔗 **[Ollama GitHub](https://github.com/ollama/ollama)** | 💬 **[Join Discord](#)**  

## 🚀 Quick Start  

### 🖥️ CPU-Only Setup  
Run Ollama in a Docker container without GPU support:  
```bash
docker run -d -v ollama:/root/.ollama -p 11434:11434 --name ollama ollama/ollama
```  

### ⚡ NVIDIA GPU Setup  
1. **Install NVIDIA Container Toolkit**  
   - **Debian/Ubuntu**  
     ```bash
     curl -fsSL https://nvidia.github.io/libnvidia-container/gpgkey \
         | sudo gpg --dearmor -o /usr/share/keyrings/nvidia-container-toolkit-keyring.gpg
     curl -s -L https://nvidia.github.io/libnvidia-container/stable/deb/nvidia-container-toolkit.list \
         | sed 's#deb https://#deb [signed-by=/usr/share/keyrings/nvidia-container-toolkit-keyring.gpg] https://#g' \
         | sudo tee /etc/apt/sources.list.d/nvidia-container-toolkit.list
     sudo apt-get update
     sudo apt-get install -y nvidia-container-toolkit
     ```  
   - **CentOS/Fedora**  
     ```bash
     curl -s -L https://nvidia.github.io/libnvidia-container/stable/rpm/nvidia-container-toolkit.repo \
         | sudo tee /etc/yum.repos.d/nvidia-container-toolkit.repo
     sudo yum install -y nvidia-container-toolkit
     ```  
2. **Configure Docker to use NVIDIA runtime**  
   ```bash
   sudo nvidia-ctk runtime configure --runtime=docker
   sudo systemctl restart docker
   ```  
3. **Start Ollama with NVIDIA GPU support**  
   ```bash
   docker run -d --gpus=all -v ollama:/root/.ollama -p 11434:11434 --name ollama ollama/ollama
   ```  

### 🔥 AMD GPU Setup (ROCm)  
Run Ollama with AMD GPU support using ROCm:  
```bash
docker run -d --device /dev/kfd --device /dev/dri -v ollama:/root/.ollama -p 11434:11434 --name ollama ollama/ollama:rocm
```  

## 🤖 Running a Model  
Once the container is running, execute models inside it:  
```bash
docker exec -it ollama ollama run llama3
```  

### 📌 Explore More Models  
Discover additional models in the **[Ollama Model Library](https://ollama.ai/library)**.  

🚀 Get started today and run LLMs with **Ollama on Docker** effortlessly!  

---
