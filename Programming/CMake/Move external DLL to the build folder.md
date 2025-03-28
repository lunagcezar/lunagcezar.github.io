---
layout: default
title:  Move external DLL to the build folder
date:   2024-04-10 12:00 -03:00
author: Luna G. Cezar
tags:
  - cmake
grand_parent: Programming
parent: CMake
---

# Move external DLL to the build folder

**Created:** 2024-04-10

After adding your executable on [[CMakeLists]], you can do a file operation with [[CMake]]:

```cmake
if(WIN32 AND (CMAKE_C_COMPILER_ID MATCHES Clang OR MSVC))
	if(EXISTS ${CMAKE_BINARY_DIR}/${CMAKE_BUILD_TYPE} AND NOT EXISTS ${CMAKE_BINARY_DIR}/${CMAKE_BUILD_TYPE}/${YOUR_DLL})
		file(COPY "${PATH_TO_DLL}" DESTINATION ${CMAKE_BINARY_DIR}/${CMAKE_BUILD_TYPE})
	endif()
	if(NOT EXISTS ${CMAKE_BINARY_DIR}/${YOUR_DLL})
		file(COPY "${PATH_TO_DLL}" DESTINATION ${CMAKE_BINARY_DIR})
	endif()
endif()
```

## Variables

**YOUR_DLL** is the name of the DLL that you want to copy

**PATH_TO_DLL** is the path of the DLL provided by the third-party library


[//begin]: # "Autogenerated link references for markdown compatibility"
[CMakeLists]: CMakeLists "CMakeLists"
[CMake]: ../CMake "CMake"
[//end]: # "Autogenerated link references"