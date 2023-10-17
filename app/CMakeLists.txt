SET(APPS
  NuHepMCXSTool
  testdist
  NuHepMC2dot)

foreach(app ${APPS})
  add_executable(${app} ${app}.cxx)
  target_link_libraries(${app} PRIVATE NuHepMC::Tools)
endforeach()

install(TARGETS ${APPS} DESTINATION bin)
