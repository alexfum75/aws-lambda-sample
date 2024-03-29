#   Copyright 2010-2019 Amazon.com, Inc. or its affiliates. All Rights Reserved.

#   This file is licensed under the Apache License, Version 2.0 (the "License").
#   You may not use this file except in compliance with the License. A copy of
#   the License is located at

#   http://aws.amazon.com/apache2.0/

#   This file is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR
#   CONDITIONS OF ANY KIND, either express or implied. See the License for the
#   specific language governing permissions and limitations under the License.

cmake_minimum_required(VERSION 3.5)

project(lambda-example)

set (CMAKE_CXX_STANDARD 11)

set(CMAKE_CXX_STANDARD_REQUIRED True)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} ${SSE_FLAGS} -march=native  -std=c++0x") 

include_directories(/home/itam/aws-sdk-cpp /home/itam/aws-sdk-cpp/aws-cpp-sdk-core/include)

# Locate the aws sdk for c++ package.
#find_package(AWSSDK REQUIRED COMPONENTS lambda)

find_package(aws-sdk-cpp)

# The executables to build.
set(EXAMPLES "")

list(APPEND EXAMPLES "lambda_example")

# The executables to build
foreach(EXAMPLE IN LISTS EXAMPLES)
  add_executable(${EXAMPLE} ${EXAMPLE}.cpp)
  target_link_libraries(${EXAMPLE} ${AWSSDK_LINK_LIBRARIES})
endforeach()
