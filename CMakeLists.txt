# MSDF gen Subdirectory
file(GLOB_RECURSE MSDF_GEN_SOURCES
		CONFIGURE_DEPENDS
		${CMAKE_CURRENT_SOURCE_DIR}/core/*.cpp
		${CMAKE_CURRENT_SOURCE_DIR}/core/*.hpp
		${CMAKE_CURRENT_SOURCE_DIR}/core/*.h
		${CMAKE_CURRENT_SOURCE_DIR}/ext/*.cpp
		${CMAKE_CURRENT_SOURCE_DIR}/ext/*.hpp
		${CMAKE_CURRENT_SOURCE_DIR}/ext/*.h
		${CMAKE_CURRENT_SOURCE_DIR}/lib/*.cpp
		${CMAKE_CURRENT_SOURCE_DIR}/include/*.h
	)

find_package(Freetype REQUIRED)

# Create MSDF gen library
add_library(msdfgen
		${MSDF_GEN_SOURCES}
	)

target_link_libraries(msdfgen
		Freetype::Freetype
	)

target_include_directories(msdfgen PUBLIC
		${CMAKE_CURRENT_SOURCE_DIR}/include	
	)

target_compile_definitions(msdfgen
		PUBLIC MSDFGEN_PUBLIC=
	)
