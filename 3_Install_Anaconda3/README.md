# 아나콘다 설치
```zsh
# 아나콘다 아카이브에 접속해 설치할 버전 확인 (https://repo.anaconda.com/archive/)

# 설치 예시 (2024.6월 버전 설치)
wget https://repo.anaconda.com/archive/Anaconda3-2024.06-1-Linux-x86_64.sh
sh Anaconda3-2024.06-1-Linux-x86_64.sh

# zsh에 PATH 추가
code ~/.zshrc

export PATH=$HOME/anaconda3/bin:$PATH
# >>> conda initialize >>>
# !! Contents within this block are managed by 'conda init' !!
__conda_setup="$('$HOME/anaconda3/bin/conda' 'shell.zsh' 'hook' 2> /dev/null)"
if [ $? -eq 0 ]; then
    eval "$__conda_setup"
else
    if [ -f "$HOME/anaconda3/etc/profile.d/conda.sh" ]; then
        . "$HOME/anaconda3/etc/profile.d/conda.sh"
    else
        export PATH="$HOME/anaconda3/bin:$PATH"
    fi
fi
unset __conda_setup
# <<< conda initialize <<<


# 아나콘다가 인식되는지 확인
conda --version
```
