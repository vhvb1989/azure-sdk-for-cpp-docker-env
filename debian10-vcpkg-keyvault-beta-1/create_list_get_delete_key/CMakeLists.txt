cmake_minimum_required (VERSION 3.13)

# clgd => create-list-get-delete
project(clgd-key LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED True)

message("-${VCPKG_TARGET_TRIPLET}  ... ${CMAKE_TOOLCHAIN_FILE}")

find_package(CURL ${CURL_MIN_REQUIRED_VERSION} REQUIRED)
find_package(azure-security-keyvault-keys-cpp CONFIG REQUIRED)
find_package(azure-identity-cpp CONFIG REQUIRED)

set(
  CLGD_KEY_SOURCE
  src/main.cpp
)

add_executable(clgd-key ${CLGD_KEY_SOURCE})

target_link_libraries(clgd-key
  PRIVATE
  Azure::azure-security-keyvault-keys
  Azure::azure-identity)
