## CMakeList 가 필요한 이유
CMakeList.txt 는 opengl 등의 필요한 프로그램(?) 버전 정보, 어떤 파일을 로드할 것인지, 어떤 라이브러리가 쓰이는지 등에 대한 정보가 쓰여있는 것  
CMake 를 로드하면 이 정보들을 기반으로 빌드 명령어를 만들어준다  
컴파일러는 이 명령어를 기계어로 바꿔줘서 그 결과 빌드파일 .exe(Windows 의 경우) 파일이 나옴

## 프로젝트의 루트 폴더 확인하는 방법
CMakeLists.txt 가 위치한 경로가 루트 디렉토리!  

## 상대 경로 에러가 생겼을 경우
절대 경로로 입력할 것.  
filesystem.h 헤더에 정의된 getPath 함수를 쓰면 된다.  

## Key1 누를 때 어케 해야하는지 모르겠음ㅜㅜ
model 이랑 Base 가 무슨 차이가 있나..?

if (RobotControl == 1  && LeftButtonDown == 1) { // key2 를 누르면...  
    model = glm::translate(model, glm::vec3())
    model = glm::rotate(glm::radians(BaseSpin), glm::vec3(0.0f, 1.0f, 0.0f));  
}  
