cmake_minimum_required(VERSION 3.19)

project(MiniWeather
        VERSION 1.0
        LANGUAGES Fortran)

add_executable(miniWeather_mpi_openacc miniWeather_mpi_openacc.F90)

set(CMAKE_Fortran_FLAGS "-O2 -fast -Minfo=all,intensity")

find_package(MPI REQUIRED)
target_link_libraries(miniWeather_mpi_openacc PUBLIC MPI::MPI_Fortran)

find_package(PkgConfig REQUIRED)
pkg_search_module(PNETCDF REQUIRED pnetcdf)

target_include_directories(miniWeather_mpi_openacc SYSTEM PUBLIC ${PNETCDF_INCLUDE_DIRS})
target_link_directories(miniWeather_mpi_openacc PUBLIC ${PNETCDF_LIBRARY_DIRS})
target_link_libraries(miniWeather_mpi_openacc PUBLIC ${PNETCDF_LIBRARIES})

find_package(OpenACC REQUIRED)
target_link_libraries(miniWeather_mpi_openacc PUBLIC OpenACC::OpenACC_Fortran)

message(STATUS "PNETCDF_LINK_LIBRARIES: ${PNETCDF_LIBRARIES}")


