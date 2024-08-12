# ext4.vhdx 파일 용량 줄이기
&nbsp;
WSL의 가상 디스크 용량은 자동으로 줄어들지 않기 때문에 주기적으로 디스크를 압축해야 컴퓨터의 용량을 확보할 수 있습니다.
```Powershell
wsl --shutdown
select vdisk file="C:\Users\(사용자 이름)\AppData\Local\Packages\(CanonicalGroupLimited으로 시작하는 Ubuntu 폴더)\LocalState\ext4.vhdx"
attach vdisk readonly
compact vdisk
detach vdisk
exit
```
