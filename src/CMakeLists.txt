IF(MSVC80 OR MSVC90)
  OPTION(OSG_MSVC_GENERATE_PLUGINS_AND_WRAPPERS_MANIFESTS "Generate or not manifests files under VS8 for dynamically loaded dlls" ON)
ENDIF()


if(Qt5Widgets_FOUND)
	add_subdirectory(osgQOpenGL)
else()
	add_subdirectory(osgQt)
endif()