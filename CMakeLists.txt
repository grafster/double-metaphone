cmake_minimum_required(VERSION 3.10)

project(double-metaphone CXX)


add_library(double-metaphone STATIC double_metaphone.cc)

target_include_directories(double-metaphone PUBLIC $<BUILD_INTERFACE:${CMAKE_CURRENT_LIST_DIR}> $<INSTALL_INTERFACE:include>)

#if(MSVC)
#  add_compile_options(/fudge)
#endif()

install(
    TARGETS double-metaphone
    EXPORT double-metaphone-targets
    RUNTIME DESTINATION bin
    LIBRARY DESTINATION lib
    ARCHIVE DESTINATION lib
)

install(FILES double_metaphone.h DESTINATION include/double-metaphone CONFIGURATIONS Release)
install(EXPORT double-metaphone-targets NAMESPACE double-metaphone:: FILE double-metaphone-targets.cmake DESTINATION share/double-metaphone)

