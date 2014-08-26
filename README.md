CMake subprojects
==================

A demonstration project using cmake to build several 
other open source cmake based projects in one go.

The project consists of a set of simple rules to 
checkout several other projects (which may depend 
on each other) and then build them as part of one 
larger cmake project. The superproject uses 
add_subdirectory(...) on each of the subprojects 
to produce a single top level project 
with each subproject as a subdirectory.



