cmake_minimum_required(VERSION 3.13)
project(pico_w_keypad_led C CXX)

set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)

# NOTE:
# The provided firmware is Arduino-style (setup/loop + Keypad.h).
# Build it with the Arduino-Pico core (Earle Philhower) or in Wokwi as an Arduino sketch.
# This CMake file documents project metadata and folder structure consistency.
