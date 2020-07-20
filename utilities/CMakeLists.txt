INCLUDE_DIRECTORIES( ${CMAKE_CURRENT_SOURCE_DIR} ${CMAKE_CURRENT_BINARY_DIR} )


########### next target ###############

SET(csv2antenna_SRCS
   csv2antenna.c
   )

ADD_EXECUTABLE(csv2antenna ${csv2antenna_SRCS})

SET(cluttergen_SRCS
   cluttergen.cpp
   )

ADD_EXECUTABLE(cluttergen ${cluttergen_SRCS})

SET(cluttergen2d_SRCS
   cluttergen2d.cpp
   )

ADD_EXECUTABLE(cluttergen2d ${cluttergen2d_SRCS})

SET(h52raw_SRCS
   h52raw.cpp
   )


ADD_EXECUTABLE(h52raw ${h52raw_SRCS})

#Link to the HDF5 libraries
find_package(HDF5 COMPONENTS HL REQUIRED)
include_directories(SYSTEM ${HDF5_INCLUDE_DIRS} ${HDF5_HL_INCLUDE_DIR})
target_link_libraries(h52raw ${HDF5_LIBRARIES} ${HDF5_HL_LIBRARIES})

########### install files ###############

#original Makefile.am contents follow:

#
#bin_PROGRAMS = csv2antenna
#csv2antenna_SOURCES = csv2antenna.c
