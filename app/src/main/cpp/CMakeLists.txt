cmake_minimum_required(VERSION 3.12)

add_library(object OBJECT
	        object.cpp)

add_library(shared SHARED
		shared.cpp)

target_link_libraries(shared
        object)

