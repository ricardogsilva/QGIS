########################################################
# Files

set (LANDINGPAGE_SRCS
  ${CMAKE_SOURCE_DIR}/external/nlohmann/json.hpp
  ${CMAKE_SOURCE_DIR}/external/inja/inja.hpp
  qgslandingpage.cpp
  qgslandingpageutils.cpp
  qgslandingpagehandlers.cpp
)

########################################################
# Build

add_library (landingpage MODULE ${LANDINGPAGE_SRCS})

include_directories(SYSTEM
)

include_directories(

  ${CMAKE_SOURCE_DIR}/src/server
  ${CMAKE_SOURCE_DIR}/src/server/services
  ${CMAKE_SOURCE_DIR}/src/server/services/landingpage

  ${CMAKE_BINARY_DIR}/src/python
  ${CMAKE_BINARY_DIR}/src/server

  ${CMAKE_CURRENT_BINARY_DIR}
)


target_link_libraries(landingpage
  qgis_core
  qgis_server
)


########################################################
# Install

install(TARGETS landingpage
    RUNTIME DESTINATION ${QGIS_SERVER_MODULE_DIR}
    LIBRARY DESTINATION ${QGIS_SERVER_MODULE_DIR}
)

