cmake_minimum_required(VERSION 3.20.0)
find_package(Zephyr REQUIRED HINTS $ENV{ZEPHYR_BASE})
project(nrf_connect_sdk_tutorial)
target_sources(app PRIVATE src/main.c)
