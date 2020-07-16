# Screamer에 대한 Hwid 변경 및 플래시

# Flashing (Xilinx/Diligent programming cable):
<img src="https://gist.githubusercontent.com/ufrisk/c5ba7b360335a13bbac2515e5e7bb9d7/raw/f806a68890c94561e53caa7758a5903bb01f5670/gh_m2_2.png"/>


1. **Vivado WebPACK** or **Lab Edition** 를 설치합니다.
2. **PCILeech ScreamerM2** 를 빌드합니다. 혹은 사전 빌드를 다운로드 합니다.
3. **Vivado Tcl Shell command promp** 를 엽니다.
4. **cd**를 통하여 압축을 푼 경로로 이동하십시오.
5. **JTAG USB cable**를 연결하십시오
6. **Run source vivado_flash_hs2.tcl -notrace** 를 입력하여 스크리머에 펌웨어를 플래시 하십시오!!


# Flashing (LambdaConcept programming cable)
 해당 케이블을 사용하는경우 OpenOCD를 권장합니다.

1. PCILeech PCIeScreamer 를 빌드하거나 사전 빌드 데이터를 다운로드 받으십시오.
2. http://docs.lambdaconcept.com/screamer/index.html 에서 OpenOCD (Linux 권장)로 플래시하는 방법에 대한 지시 사항을 따르십시오 .


# 빌드

1. **Xilinx Vivado WebPACK 2020.1** or later 설치 
2. **Vivado Tcl Shell command prompt** 를 여십시오
3. cd 명령어로  ScreamerM2의 경로로 이동
4. Run source vivado_generate_project.tcl -notrace 로 프로젝트 파일을 생성하십시오
5. Run source vivado_build.tcl -notrace to 로 자일링스 고유의 ip 코어 및 빌드스트림 생성


 
