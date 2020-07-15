개인적으로 프로그래밍 하기위해 정리한 문서

# PCILeechCustomFirmware 
  해당 문서는 PCILeech의 커스텀 펌웨어를 만드는 방법에 대해서 소개합니다.  
  해당 문서는 자일링스의 SP605를 사용합니다.
  
## Flashing
<img src="https://gist.githubusercontent.com/ufrisk/c5ba7b360335a13bbac2515e5e7bb9d7/raw/d01be0e485fde5ba09d84be35ca2970038e18577/_gh_fpga_ft601.jpg" height="300"/><img src="https://gist.githubusercontent.com/ufrisk/c5ba7b360335a13bbac2515e5e7bb9d7/raw/d01be0e485fde5ba09d84be35ca2970038e18577/_gh_fpga_sp605.jpg" height="300"/>

- 먼저 위와 같이 올바르게 스위치를 구성해야합니다

- 그 뒤 **Xilinx ISE** 개발 환경을 설치합니다.  
- PCILeech SP605 를 빌드하거나 혹은 사전 빌드된 바이너리를 다운로드하고 압축 해제합니다

- 사전 빌드된 바이너리 주소 : https://mega.nz/#!QPJm3bLT!8NrEBR-yLn-Qur7VkqsnahiPgkGp2nWw4Z9XWLLamxo

- 그 뒤 **ISE Design Suite 64** 명령 프롬톰트를 실행합니다. 또한 JTAG USB 케이블이 연결되어 있는지 확인해야합니다. 
- 이후 **SP605**에 비트스트림을 플래시 시키기위해 **flash.bat**을 실행합니다

## 빌드 하는법
 - **ISE Design Suite 64** 프롬톰트를 엽니다
 - **build.bat** 을 실행하여 자일링스 고유의 IP 코어 및 빌드 비트 스트림을 생성 할 수 있습니다.
 - 완료
 
 
## Device ID 바꾸는법

 - 위와 같이 빌드를 먼저 수행합니다
 - 프로젝트에서 **pcileech_sp605.xise** 를 더블 클릭해서 엽니다.
 - 도구(Tool) -> Core Generator 를 눌러 코어 제네레이터르 엽니다
 - 코어 제네레이터에서 s6_pcie_v2_4 를 더블클릭합니다.
 - PCI Express 용 Spartan-6 통합 블록 마법사에서 9 페이지 중 3 페이지로 건너 뛰고 값을 원하는 값으로 변경합니다
 - 값을 변경한후 'Generator'를 누릅니다.
 - 변경된 PCIe를 성공적으로 재생성 한 후 Core Generator 및 ISE Design Suite를 닫습니다.
 - ISE Design Suite 64 비트 명령 프롬프트를 엽니 다.
 - Run: xtclsh pcileech_sp605.tcl rebuild_project      로 새로운 프로젝트 생성
 - Run: promgen -w -p mcs -c FF -o pcileech -s 8192 -u 0000 pcileech_top.bit -spi       로 플래싱을 위한 새로운 mcs파일들을 만드십시오
 - Run: flash.bat 를 실행하여 새로운 .mcs 파일을 보드에 플래싱 시킵니다. :)
 
 
## 이상입니다.

 여기까지 완료하였다면 자일링스를 멀웨어로 감지할 수 없습니다.
