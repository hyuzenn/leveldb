cmake_minimum_required(VERSION 3.5.0)
project(leveldb_bench VERSION 0.1.0 LANGUAGES C CXX)

# 디버그 모드 설정
set(CMAKE_BUILD_TYPE Debug)

# LevelDB 경로 설정
include_directories(
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/include
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/util 
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/port
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/db
)

# 소스 파일 추가
set(SOURCES
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/main.cpp
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/db/db_impl.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/db/log_reader.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/db/log_writer.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/include/leveldb/filter_policy.h
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/db/version_edit.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/util/crc32c.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/db/memtable.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/db/version_edit.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/db/version_set.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/util/logging.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/table/iterator.cc  
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/table/merger.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/table/table.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/table/format.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/table/block_builder.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/table/block.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/table/filter_block.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/table/filter_block_test.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/table/table_builder.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/table/table_test.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/table/two_level_iterator.cc
)

# LevelDB 라이브러리 생성
add_library(leveldb ${SOURCES})

# 실행 파일 생성 및 링킹
add_executable(leveldb_bench /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/main.cpp)
target_link_libraries(leveldb_bench leveldb)

# 헤더 파일 포함
target_include_directories(leveldb_bench PRIVATE /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/db)

# 실행 파일에 대한 디버그 모드 설정
set_target_properties(leveldb_bench PROPERTIES DEBUG_OUTPUT "debug_output")

# C++11 ABI 설정
add_definitions(-D_GLIBCXX_USE_CXX11_ABI=0)

# Google Test 설정
find_package(GTest REQUIRED)
include_directories(${GTEST_INCLUDE_DIRS})

# 테스트 실행 파일 및 링크 설정
add_executable(table_test /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/table/table_test.cc)
target_link_libraries(table_test ${GTEST_LIBRARIES} pthread leveldb)
