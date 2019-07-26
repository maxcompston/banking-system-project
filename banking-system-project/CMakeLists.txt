cmake_minimum_required (VERSION 2.8)
project (BankSystem)

#version number
set (BankSystem_VERSION_MAJOR 2)
set (BankSystem_VERSION_MINOR 0)

#include the subdirectory containing our libs
add_subdirectory (Account)
include_directories(Account)
add_library(Account::library ALIAS Account)
#indicate the entry point for the executable
add_executable (BankSystem bank-management-system.cpp)

# Indicate which libraries to include during the link process.
target_link_libraries (BankSystem
    PRIVATE
        Account::library)

install (TARGETS BankSystem DESTINATION bin)
