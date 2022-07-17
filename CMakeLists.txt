cmake_minimum_required(VERSION 3.0.2)
project(buckle C)

set(PATH_AUDIO ./wav)
set(VERSION 1.5.1)
set(EXE buckle)

add_compile_definitions(PATH_AUDIO="${PATH_AUDIO}")
add_compile_definitions(VERSION="${VERSION}")

find_package(OpenAL)
find_library(ALURE_LIBRARY ALURE32)

message(STATUS "${OPENAL_INCLUDE_DIR}")
message(STATUS "${OPENAL_LIBRARY}")
message(STATUS "${ALURE_LIBRARY}")

include_directories(
  inc
  ${OPENAL_INCLUDE_DIR}
)

add_executable(${EXE} src/main.c src/scan-windows.c)
target_link_libraries(
  ${EXE}
  ${OPENAL_LIBRARY}
  ${ALURE_LIBRARY}
)
