# CUDA 11.8, CUDNN 설치 후 적용
```zsh
# 다운로드 후 실행
wget https://developer.download.nvidia.com/compute/cuda/11.8.0/local_installers/cuda_11.8.0_520.61.05_linux.run
sudo sh cuda_11.8.0_520.61.05_linux.run

# CUDA 설치됐는지 확인
$ ls /usr/local/ | grep cuda

# 다운로드 후 압축 해제
wget https://developer.download.nvidia.com/compute/cudnn/redist/cudnn/linux-x86_64/cudnn-linux-x86_64-9.0.0.312_cuda11-archive.tar.xz
tar -xvf cudnn-linux-x86_64-9.0.0.312_cuda11-archive.tar.xz

# 올바른 CUDA 폴더에 넣기
cd cudnn-linux-x86_64-9.0.0.312_cuda11-archive
sudo cp include/cudnn*.h /usr/local/cuda-11.8/include
sudo cp lib/libcudnn* /usr/local/cuda-11.8/lib64

# PATH 설정하기
code ~/.zshrc

# 맨 끝에 2줄 추가하기
export PATH="/usr/local/cuda-11.8/bin:$PATH"
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/cuda-11.8/lib64/

# CUDA가 제대로 인식되는지 확인
nvcc --version

# 필요없는 파일 삭제 (무서우면 파일 탐색기로 삭제하기)
rm cuda_11.8.0_520.61.05_linux.run
rm -rf cudnn-linux-x86_64-9.0.0.312_cuda11-archive
```
&nbsp;
&nbsp;

# 다른 버전의 CUDA와 CUDNN을 설치하고 싶다면…
```zsh
# https://developer.nvidia.com/cuda-toolkit-archive에서 원하는 버전의 CUDA를 설치
# Linux / x86_64 / WSL-Ubuntu / 2.0 / runfile (local)을 선택한 뒤 명령어 실행

# CUDNN 12 버전
wget https://developer.download.nvidia.com/compute/cudnn/redist/cudnn/linux-x86_64/cudnn-linux-x86_64-9.0.0.312_cuda12-archive.tar.xz
tar -xvf cudnn-linux-x86_64-9.0.0.312_cuda12-archive.tar.xz

# CUDA 버전을 여러 개 설치하고 필요에 따라 바꾸고 싶다면
code ~/.zshrc

# zshrc에 _switch_cuda 함수 추가
function _switch_cuda {
   v=$1
   export PATH=$PATH:/usr/local/cuda-$v/bin
   export CUDADIR=/usr/local/cuda-$v
   export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/cuda-$v/lib64
   nvcc --version
}

# CUDA 버전 바꾸기
_switch_cuda (버전 숫자)
```

# 주의사항
1. nvidia-smi을 통해 보여지는 CUDA 버전은 설치된 CUDA 버전이 아닌 현재 환경에 가장 적합한 CUDA 버전을 추천하는 것입니다.
2. ```zsh
   Command 'nvcc' not found, but can be installed with:
   sudo apt install nvidia-cuda-toolkit
   ```
   이러한 에러가 발생했을 때 nvidia-cuda-toolkit을 설치하는 것은 딱히 도움이 되지 않습니다.
