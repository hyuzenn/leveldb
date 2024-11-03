cmake_minimum_required(VERSION 3.5.0)
project(leveldb_bench VERSION 0.1.0 LANGUAGES C CXX)

# C++11 표준 설정
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED True)
add_definitions(-D_GLIBCXX_USE_CXX11_ABI=0)

# 디버그 모드 설정
set(CMAKE_BUILD_TYPE Debug)

# LevelDB 경로 설정
include_directories(
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/include
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/util 
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/port
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/db
    ${PROJECT_SOURCE_DIR}/include
    ${PROJECT_SOURCE_DIR}/third_party/googletest/include
    ${PROJECT_SOURCE_DIR}/third_party/googletest/googlemock/include
    ${PROJECT_SOURCE_DIR}/leveldb/include
    ${PROJECT_SOURCE_DIR}/leveldb/include/leveldb
)

# 소스 파일 추가
set(SOURCES
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/main.cpp

    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/db/db_impl.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/db/log_reader.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/db/log_writer.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/db/memtable.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/db/version_edit.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/db/version_set.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/db/autocompact_test.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/db/builder.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/db/c.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/db/corruption_test.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/db/db_iter.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/db/db_test.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/db/dbformat_test.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/db/dbformat.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/db/dumpfile.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/db/fault_injection_test.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/db/filename_test.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/db/filename.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/db/leveldbutil.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/db/log_test.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/db/recovery_test.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/db/repair.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/db/skiplist_test.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/db/table_cache.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/db/version_edit_test.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/db/version_set_test.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/db/version_set.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/db/write_batch_test.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/db/write_batch.cc

    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/include/leveldb/filter_policy.h

    mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/util/arena_test.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/util/arena.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/util/bloom_test.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/util/bloom.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/util/cache_test.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/util/cache.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/util/coding_test.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/util/coding.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/util/comparator.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/util/crc32c_test.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/util/env_posix_test.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/util/env_posix.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/util/env_test.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/util/env_windows_test.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/util/env_windows.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/util/env.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/util/filter_policy.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/util/hash_test.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/util/hash.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/util/histogram.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/util/logging_test.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/util/no_destructor_test.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/util/options.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/util/status_test.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/util/status.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/util/testutil.cc
    /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/util/crc32c.cc
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
target_include_directories(leveldb_bench PUBLIC /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/include)

# C++11 ABI 설정
add_definitions(-D_GLIBCXX_USE_CXX11_ABI=0)

# Google Test 경로 수동 설정
set(GTEST_ROOT "C:/Users/huj22/source/repos/sp24f/linking_lab/leveldb/third_party/googletest")
find_library(GTEST_LIBRARY gtest HINTS ${GTEST_ROOT}/lib)
find_library(GTEST_MAIN_LIBRARY gtest_main HINTS ${GTEST_ROOT}/lib)
include_directories(${GTEST_ROOT}/include)
include_directories(${GTEST_ROOT}/googlemock/include)

# 테스트 실행 파일 및 링크 설정
add_executable(table_test /mnt/c/Users/huj22/source/repos/sp24f/linking_lab/leveldb/table/table_test.cc)
target_link_libraries(table_test ${GTEST_LIBRARY} ${GTEST_MAIN_LIBRARY} pthread leveldb)

find_package(GTest REQUIRED)
include_directories(${GTEST_INCLUDE_DIRS})
