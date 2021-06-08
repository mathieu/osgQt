#######################################################
# this are setting used in SETUP_EXAMPLE macro
#######################################################
SET(TARGET_DEFAULT_PREFIX "example_")
SET(TARGET_DEFAULT_LABEL_PREFIX "Examples")

IF(DYNAMIC_OPENSCENEGRAPH)

ADD_SUBDIRECTORY(osgviewerQt)

ENDIF()

