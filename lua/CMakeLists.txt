PROJECT(Lua)

#Cmake version dependency checking
IF( ${CMAKE_MINOR_VERSION} GREATER 4 )
	CMAKE_POLICY(SET CMP0005 OLD)
ENDIF( ${CMAKE_MINOR_VERSION} GREATER 4 )


#3rd partys and additional include paths
SET(3rdParty_DIR ${Lua_SOURCE_DIR}/../../3rdParty CACHE PATH "3rdParty Directory")
INCLUDE_DIRECTORIES(${3rdParty_DIR})
INCLUDE_DIRECTORIES(${UIViews_SOURCE_DIR})
INCLUDE_DIRECTORIES(${UIViews_SOURCE_DIR}/cmake/lua/Src/)
INCLUDE_DIRECTORIES(../)


FILE(GLOB ALL_C "./Src/*.c")
SOURCE_GROUP(Src FILES ${ALL_C})
FILE(GLOB ALL_H "./Src/*.h")
SOURCE_GROUP(Src FILES ${ALL_H})


#Build and dependencies definition
ADD_LIBRARY(Lua STATIC
	${ALL_C}
        ${ALL_H}
)