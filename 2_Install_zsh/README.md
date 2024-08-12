# zsh 설치 및 커스터마이징
&nbsp;
```zsh
# zsh 설치
sudo apt-install zsh

# oh my zsh 설치
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

# bash와 zsh를 바꿔가며 사용하고 싶다면...
chsh -s $(which zsh) # 기본 셸을 zsh로
chsh -s $(which bash) # 기본 셸을 bash로

# 터미널 테마 모음집 사이트 (https://terminalsplash.com)

# PowerLevel10k 설치
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k

# PowerLevel10k에 필요한 폰트 설치 후 터미널에 적용
# https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Regular.ttf
```

자세한 커스터마이징에 대해선 아래 영상들을 참고해주세요. (이미지를 클릭하면 영상으로 이동합니다.)


[![Video Label](https://img.youtube.com/vi/o2Mji64i2Ms/maxresdefault.jpg)](https://www.youtube.com/watch?v=o2Mji64i2Ms)
[![Video Label](https://img.youtube.com/vi/UAUg0K5fc3Y/maxresdefault.jpg)](https://www.youtube.com/watch?v=UAUg0K5fc3Y)
[![Video Label](https://img.youtube.com/vi/Qn0oHSMzcz4/maxresdefault.jpg)](https://www.youtube.com/watch?v=Qn0oHSMzcz4)
