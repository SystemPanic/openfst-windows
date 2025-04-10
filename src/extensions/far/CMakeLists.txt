file(GLOB HEADER_FILES ../../include/fst/extensions/far/*.h)
message(STATUS "${HEADER_FILES}")

add_library(fstfar
  sttable.cc
  stlist.cc
  ${HEADER_FILES}
)
target_link_libraries(fstfar fst)
set_target_properties(fstfar PROPERTIES 
  SOVERSION "${SOVERSION}"
  FOLDER far
)

install(TARGETS fstfar
  LIBRARY DESTINATION lib
  ARCHIVE DESTINATION lib
  RUNTIME DESTINATION lib
)

if(HAVE_SCRIPT)
  add_library(fstfarscript
    far-class.cc 
    farscript.cc
    getters.cc 
    script-impl.cc
    compile-strings.cc
  )
  target_link_libraries(fstfarscript fstfar fstscript fst)
  set_target_properties(fstfarscript PROPERTIES 
    SOVERSION "${SOVERSION}"
    FOLDER far
  )

  install(TARGETS fstfarscript
	LIBRARY DESTINATION lib
	ARCHIVE DESTINATION lib
	RUNTIME DESTINATION lib
  )
endif(HAVE_SCRIPT)

if(HAVE_BIN)
  function (add_executable2 _name)
      add_executable(${ARGV})
      if (TARGET ${_name})
          target_link_libraries(${_name} fstfarscript fstscript fst ${CMAKE_DL_LIBS})
          set_target_properties(${_name} PROPERTIES FOLDER far/bin)
      endif()
      install(TARGETS ${_name} RUNTIME DESTINATION bin)
  endfunction()

  add_executable2(farcompilestrings farcompilestrings.cc farcompilestrings-main.cc)
  add_executable2(farconvert  farconvert.cc farconvert-main.cc)
  add_executable2(farcreate  farcreate.cc farcreate-main.cc)
  add_executable2(farequal  farequal.cc farequal-main.cc)
  add_executable2(farencode  farencode.cc farencode-main.cc)
  add_executable2(farextract  farextract.cc farextract-main.cc)
  add_executable2(farinfo  farinfo.cc farinfo-main.cc)
  add_executable2(farisomorphic  farisomorphic.cc farisomorphic-main.cc)
  add_executable2(farprintstrings  farprintstrings.cc farprintstrings-main.cc)
endif(HAVE_BIN)



