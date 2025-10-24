## CMakeList 가 필요한 이유
CMakeList.txt 는 opengl 등의 필요한 프로그램(?) 버전 정보, 어떤 파일을 로드할 것인지, 어떤 라이브러리가 쓰이는지 등에 대한 정보가 쓰여있는 것  
CMake 를 로드하면 이 정보들을 기반으로 빌드 명령어를 만들어준다  
컴파일러는 이 명령어를 기계어로 바꿔줘서 그 결과 빌드파일 .exe(Windows 의 경우) 파일이 나옴

## 프로젝트의 루트 폴더 확인하는 방법
CMakeLists.txt 가 위치한 경로가 루트 디렉토리!  

## 상대 경로 에러가 생겼을 경우
절대 경로로 입력할 것.  
filesystem.h 헤더에 정의된 getPath 함수를 쓰면 된다.  

## assimp 폴더명 주의  
mac 에서 돌릴 경우에는 macos 에 설치된 assimp 을 돌릴 예정이기 때문에 현재폴더의 assimp 는 무시합니다  
즉, includes/assimp_OLD 로 수정할 것  
windows 에서 돌릴 경우에는 다시 assimp 으로 수정해서 돌려야 에러가 나지 않습니다.  

## macos 에서 CLion 을 돌리면 MinGW 툴체인 오류가 발생하지 않는데, windows 에서는 발생하는 이유
툴체인이란?  
코드를 실행 파일로 바꿔주는 도구 세트. 아래의 세 가지로 구성:  
- 컴파일러
- 링커
- 표준 라이브러리/런타임
macOS 에서는 한 가지 툴체인 규격으로 굴러간다  
기본적으로 Apple Clang + clang 링커 + libc++ 로 구성되어있고, 같은 규격이기 떄문에 안 섞이고 잘 맞는다  
반면, windows 에서는 두 계열이 있다  
MSVC 계열: Visual Studio 가 제공하며, 라이브러리는 보통 .lib 파일  
MinGW / GCC 계열: MSYS2/MinGW 가 제공하며, 라이브러리는 보통 .a 혹은 .dll.a 파일  
이 두 계열의 규격(이름 장식이나 런타임 등)이 다르기 때문에 서로 만든 라이브러리끼리 호환되지 않는다  
따라서 기존에 CLion 에서 default 로 설정된 MinGW 툴체인으로 .lib 파일들을 붙이려다보니 호환되지 않아 에러가 발생한다  
따라서 한 가지 계열로 통일시켜야하고, 이 때문에 Visual Studio Installer 를 통해 MSVC 계열로 맞춰준 것이다  