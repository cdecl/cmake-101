cmake_minimum_required(VERSION 3.5)
project(main)  # 프로젝트 이름 및 사용 언어

set(CMAKE_CXX_STANDARD 17)        # C++17 사용 (필요에 따라 변경 가능)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)      # 컴파일러 확장 비활성화 (순수한 C++ 표준 준수)

# 빌드 유형 기본 설정 (없을 경우 디버그)
if(NOT CMAKE_BUILD_TYPE)
    set(CMAKE_BUILD_TYPE Release CACHE STRING "Build type" FORCE)
endif()

# 소스 코드 및 헤더 파일 포함
set(SRC_FILES src/main.cpp) 
set(HDR_FILES include/my_header.h)

# 실행 파일 생성
add_executable(${PROJECT_NAME} ${SRC_FILES} ${HDR_FILES})

# include 디렉토리 추가
target_include_directories(${PROJECT_NAME} PRIVATE include)
target_link_libraries(${PROJECT_NAME} PRIVATE pthread)  

# 최적화 옵션 설정 (빌드 유형에 따라 적용)
if(CMAKE_BUILD_TYPE STREQUAL "Debug")
    target_compile_definitions(${PROJECT_NAME} PRIVATE DEBUG_MODE)
    target_compile_options(${PROJECT_NAME} PRIVATE -Wall -Wextra -Wpedantic)
elseif(CMAKE_BUILD_TYPE STREQUAL "Release")
    target_compile_definitions(${PROJECT_NAME} PRIVATE RELEASE_MODE)
    target_compile_options(${PROJECT_NAME} PRIVATE -O2)  # 최적화 옵션
endif()

