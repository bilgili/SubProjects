project(test_subprojects)

#--------------------------------------------------
# cmake old/new compatibility
#--------------------------------------------------
cmake_minimum_required(VERSION 2.8)

#--------------------------------------------------
# load script for checking out projects from git 
#--------------------------------------------------
include(${PROJECT_SOURCE_DIR}/CMake/GitExternal.cmake)

#--------------------------------------------------
# checkout common cmake tools library
# args are : location here, repo URL, repo branch
#--------------------------------------------------
Git_External(
  ${PROJECT_SOURCE_DIR}/CMake/common 
  https://github.com/Eyescale/CMake.git
  subproject
  VERBOSE
)

#--------------------------------------------------
# checkout projects we want to build together
#--------------------------------------------------
Git_External(
  ${PROJECT_SOURCE_DIR}/Lunchbox 
  https://github.com/Eyescale/Lunchbox.git 
  master
  VERBOSE
)
Git_External(
  ${PROJECT_SOURCE_DIR}/Collage 
  https://github.com/Eyescale/Collage.git 
  master
  VERBOSE
)
#--------------------------------------------------
# support testing
#--------------------------------------------------
include(CTest)

#--------------------------------------------------
# load add_subproject macro from common tools
#--------------------------------------------------
include(${PROJECT_SOURCE_DIR}/CMake/common/SubProject.cmake)

#--------------------------------------------------
# Add the subprojects to our project
# args are : project name in subproject, path from here
#--------------------------------------------------
add_subproject(Lunchbox)
add_subproject(Collage)

