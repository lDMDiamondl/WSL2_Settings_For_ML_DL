# 파이토치 설치
&nbsp;
```zsh
conda install pytorch torchvision torchaudio pytorch-cuda=(쿠다 버전) -c pytorch -c nvidia

# 파이토치가 GPU를 인식하는지 확인
python
import torch
torch.cuda.is_available() # True가 뜨면 정상적으로 인식된 것
torch.cuda.device_count() # 사용 가능한 GPU 개수 출력 (개인은 쓸 일 거의 없음)
```
