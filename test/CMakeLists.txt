
set(TEST_SOURCES
    Foo/test.Foo.cpp
    ../src/Foo.cpp # how to remove this?
)

set(TEST_NAME TestFoo)
#  add_definitions(-DGTEST_LANGUAGE_CXX11)
add_executable(${TEST_NAME} ${TEST_SOURCES})
add_test(Tester ${TEST_NAME})
message("Tests included")

#
set(INCLUDES ../include)
include_directories(PUBLIC ${INCLUDES})
target_include_directories(${PROJECT_NAME} PUBLIC ${INCLUDES})

#  # Link googletest with the current project
#  #target_link_libraries(${PROJECT_NAME} gtest gmock )

#target_compile_features(starter_cpp PRIVATE cxx_lambda_init_captures)
