set(HEADERS
  DistributionUtils.hxx)

set(IMPLEMENTATION 
  DistributionUtils.cxx)

add_library(nuhepmc_tools STATIC ${IMPLEMENTATION})
target_link_libraries(nuhepmc_tools PUBLIC NuHepMC::CPPUtils_static)
target_link_libraries(nuhepmc_tools PRIVATE fmt)
target_compile_definitions(nuhepmc_tools PRIVATE FMT_HEADER_ONLY)
target_include_directories(nuhepmc_tools PUBLIC 
    $<BUILD_INTERFACE:${CMAKE_CURRENT_LIST_DIR}/..>
    $<BUILD_INTERFACE:${PROJECT_BINARY_DIR}/include> 
    $<INSTALL_INTERFACE:include>)
add_library(NuHepMC::Tools ALIAS nuhepmc_tools)

install(FILES ${HEADERS} DESTINATION include/NuHepMC)
