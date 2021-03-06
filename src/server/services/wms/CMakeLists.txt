
########################################################
# Files

SET (WMS_SRCS
  qgswms.cpp
  qgswmsutils.cpp
  qgsdxfwriter.cpp
  qgswmsdescribelayer.cpp
  qgswmsgetcapabilities.cpp
  qgswmsgetcontext.cpp
  qgswmsgetfeatureinfo.cpp
  qgswmsgetlegendgraphics.cpp
  qgswmsgetmap.cpp
  qgswmsgetprint.cpp
  qgswmsgetschemaextension.cpp
  qgswmsgetstyles.cpp
  qgsmaprendererjobproxy.cpp
  qgsmediancut.cpp
  qgswmsrenderer.cpp
  qgswmsparameters.cpp
  qgswmsrestorer.cpp
  qgswmsrendercontext.cpp
)

SET (WMS_HDRS
  qgswmsparameters.h
  qgswmsserviceexception.h
)

########################################################
# Build

ADD_LIBRARY (wms MODULE ${WMS_SRCS} ${WMS_HDRS})


INCLUDE_DIRECTORIES(SYSTEM
  ${GDAL_INCLUDE_DIR}
  ${POSTGRES_INCLUDE_DIR}
)

INCLUDE_DIRECTORIES(
  ${CMAKE_SOURCE_DIR}/external
  ${CMAKE_SOURCE_DIR}/external/nlohmann
  ${CMAKE_SOURCE_DIR}/src/core
  ${CMAKE_SOURCE_DIR}/src/core/annotations
  ${CMAKE_SOURCE_DIR}/src/core/expression
  ${CMAKE_SOURCE_DIR}/src/core/dxf
  ${CMAKE_SOURCE_DIR}/src/core/expression
  ${CMAKE_SOURCE_DIR}/src/core/geometry
  ${CMAKE_SOURCE_DIR}/src/core/labeling
  ${CMAKE_SOURCE_DIR}/src/core/metadata
  ${CMAKE_SOURCE_DIR}/src/core/raster
  ${CMAKE_SOURCE_DIR}/src/core/symbology
  ${CMAKE_SOURCE_DIR}/src/core/effects
  ${CMAKE_SOURCE_DIR}/src/core/layertree
  ${CMAKE_SOURCE_DIR}/src/core/layout
  ${CMAKE_SOURCE_DIR}/src/gui
  ${CMAKE_SOURCE_DIR}/src/gui/editorwidgets
  ${CMAKE_SOURCE_DIR}/src/gui/editorwidgets/core
  ${CMAKE_SOURCE_DIR}/src/server
  ${CMAKE_SOURCE_DIR}/src/server/services
  ${CMAKE_SOURCE_DIR}/src/server/services/wms

  ${CMAKE_BINARY_DIR}/src/core
  ${CMAKE_BINARY_DIR}/src/gui
  ${CMAKE_BINARY_DIR}/src/python
  ${CMAKE_BINARY_DIR}/src/analysis
  ${CMAKE_BINARY_DIR}/src/server
  ${CMAKE_CURRENT_BINARY_DIR}
)


TARGET_LINK_LIBRARIES(wms
  qgis_core
  qgis_server
)


########################################################
# Install

INSTALL(TARGETS wms
    RUNTIME DESTINATION ${QGIS_SERVER_MODULE_DIR}
    LIBRARY DESTINATION ${QGIS_SERVER_MODULE_DIR}
)

