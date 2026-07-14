cmake_minimum_required(VERSION 3.10)
project(O2EM_Web VERSION 1.0)

set(CMAKE_C_STANDARD 11)
set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -sUSE_SDL=3")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -sUSE_SDL=3")
set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -O3")
set(CMAKE_EXE_LINKER_FLAGS "${CMAKE_EXE_LINKER_FLAGS} -O3 -sUSE_SDL=3 -sALLOW_MEMORY_GROWTH=1 -sASYNCIFY=1")

set(EMCC_LINKER_OPTS 
    "-sEXPORTED_FUNCTIONS=['_main']"   
    "-sEXPORTED_RUNTIME_METHODS=['ccall','cwrap','FS']"
    "--preload-file ${CMAKE_SOURCE_DIR}/BIOS@/BIOS"
    "-sFORCE_FILESYSTEM=1"
)

string(REPLACE ";" " " EMCC_LINKER_OPTS_STR "${EMCC_LINKER_OPTS}")
set(CMAKE_EXE_LINKER_FLAGS "${CMAKE_EXE_LINKER_FLAGS} ${EMCC_LINKER_OPTS_STR}")

set(SOURCES
    rom_browser.cpp
    launcher.cpp
    input_sdl.cpp
    keyboard_sdl.cpp
	input_manager.cpp
	o2em_keymap.cpp
	o2em_keyboard_bridge.cpp
	timing_sdl.cpp
	timefunc_sdl.cpp
	vpp_stub.cpp
	voice_stub.cpp
	debug_stub.cpp
	vdc_stub.cpp
	port_stub.cpp
	main.cpp
	emulator_core.cpp
	cset.cpp
	videopac_font.cpp
	audio_sdl.cpp
	settings.cpp
	cpu.cpp
	vmachine.cpp
	crc32.cpp  
)

add_executable(o2em.html ${SOURCES})
target_link_libraries(o2em.html SDL3)