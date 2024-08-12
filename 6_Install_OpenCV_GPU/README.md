# OpenCV with GPU 설치 (어렵고 한 번에 안 될 수 있습니다. 가급적이면 개발 환경 세팅 초기에 실행하는 것을 권장합니다.)
&nbsp;
```zsh
# 패키지 업그레이드 및 설치

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install build-essential cmake
sudo apt-get install pkg-config
sudo apt-get install libjpeg-dev libtiff5-dev libpng-dev
sudo apt-get install ffmpeg libavcodec-dev libavformat-dev libswscale-dev libxvidcore-dev libx264-dev libxine2-dev
sudo apt-get install libv4l-dev v4l-utils
sudo apt-get install libgstreamer1.0-dev libgstreamer-plugins-base1.0-dev
sudo apt-get install libgtk-3-dev
sudo apt-get install libatlas-base-dev gfortran libeigen3-dev
sudo apt-get install python3-dev python3-numpy
sudo apt install unzip

# NVIDIA VIDEO CODEC SDK 설치
# https://developer.nvidia.com/nvidia-video-codec-sdk/download에서 다운로드한 폴더를 home 디렉토리로 옮긴 뒤, 폴더 디렉토리로 들어가 cuda에 복사
# 주의) 파일 탐색기를 이용해 파일을 옮길 수 없으므로 명령어를 반드시 사용할 것!!
sudo cp -rf * /usr/local/cuda/include

# <아나콘다_설치_경로>/envs/<가상환경_이름>/lib/python<버전>/site-packages/로 이동
git clone --recursive https://github.com/opencv/opencv-python.git

# (그래픽 카드 이름) compute capability를 구글링해서 찾을 것 (필자의 경우 8.9)
# 빌드에 시간이 조금 걸림
ENABLE_CONTRIB=1 python setup.py bdist_wheel -- \
	-DWITH_CUDA=ON \
	-DWITH_CUDDN=ON \
	-DOPENCV_DNN_CUDA=ON \
	-DENABLE_FAST_MATH=1 \
	-DCUDA_FAST_MATH=1 \
	-DWITH_CUBLAS=1 \
	-DCUDA_ARCH_BIN=<구글링한 compute capability로 변경> -- \
	-j $(nproc)
	
# 빌드가 끝나면 whl 파일을 실행해 OpenCV 설치
# 본인이 같은 파이썬 버전을 계속 사용할 거면 whl 파일을 백업해뒀다가
# 다시 세팅할 일 있으면 그 whl 파일로 바로 설치하는 것도 좋음
cd dist
python -m pip install --upgrade --force-reinstall (whl 파일 이름)

# OpenCV가 gpu를 인식하는지 확인
python
import cv2
cv2.cuda.getCudaEnabledDeviceCount() # 0이 아닌 숫자가 뜨면 정상적으로 인식된 것

# 만약 import 과정에서 libstdc++.so.6: version `glibcxx_3.4.30' not found 에러가 발생한다면...
conda install -c conda-forge gcc=12.1.0
```
