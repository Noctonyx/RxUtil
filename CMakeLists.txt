cmake_minimum_required(VERSION 3.15)

add_library(RXUtil STATIC
    "src/Log.h"
    "src/DampedFloat.h"
    src/Pooler.h
    src/Hasher.h
    src/Log.cpp
    src/Util.h
        )

#target_compile_features(RXUtil PRIVATE cxx_std_20)
#target_compile_options(RXUtil PUBLIC -DRX_ASSET_DIR="${PROJECT_SOURCE_DIR}/assets")

if (MSVC)
    target_compile_options(RXUtil PRIVATE /W4 /wd4275 /wd4305 /wd4310 -D_CRT_SECURE_NO_WARNINGS -D_SILENCE_CXX17_OLD_ALLOCATOR_MEMBERS_DEPRECATION_WARNING -DWIN32_LEAN_AND_MEAN)
endif ()

#target_compile_options(RXUtil PUBLIC -DSPDLOG_ACTIVE_LEVEL=0)

target_include_directories(RXUtil PUBLIC "src")

target_link_libraries(RXUtil PUBLIC spdlog::spdlog_header_only)

#set_target_properties(RXUtil PROPERTIES CXX_STANDARD 20 CXX_EXTENSIONS ON )
