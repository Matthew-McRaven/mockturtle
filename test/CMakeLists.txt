file(GLOB_RECURSE FILENAMES *.cpp)

add_executable(run_mockturtle_tests ${FILENAMES})
target_link_libraries(run_mockturtle_tests PUBLIC mockturtle catch)
if(ENABLE_COVERAGE)
  target_link_libraries(run_mockturtle_tests PUBLIC gcov)
endif()
target_compile_definitions(
  run_mockturtle_tests
  PUBLIC BENCHMARKS_PATH="${CMAKE_CURRENT_SOURCE_DIR}/../experiments/benchmarks"
)
target_compile_definitions(run_mockturtle_tests
                           PUBLIC CATCH_CONFIG_CONSOLE_WIDTH=300)
