cmake_minimum_required(VERSION 3.0)

project(pyleveldb VERSION 1.1.18)
string(TOUPPER ${PROJECT_NAME} PROJECT_NAME_UPPER)

include(GitRepoDownloadScheme)

# using cmake to build
include(CMakeScheme)

# a download target
add_download_target(URL "https://github.com/willyd/py-leveldb-windows.git"
		            TAG master
					)

ExternalProject_Get_Property("${PROJECT_NAME}_download" SOURCE_DIR)

# add build targets
add_build_targets(CMAKE_ARGS -DCMAKE_DEBUG_POSTFIX=d
				  DEPENDS leveldb)
                    
