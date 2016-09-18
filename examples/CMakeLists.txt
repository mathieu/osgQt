#######################################################
# this are setting used in SETUP_EXAMPLE macro
#######################################################
SET(TARGET_DEFAULT_PREFIX "example_")
SET(TARGET_DEFAULT_LABEL_PREFIX "Examples")

SET(TARGET_COMMON_LIBRARIES
    osgQt
)

IF(DYNAMIC_OPENSCENEGRAPH)
   
    IF   ( (QT4_FOUND OR Qt5Widgets_FOUND) AND NOT OSG_GLES1_AVAILABLE AND NOT OSG_GLES2_AVAILABLE AND NOT OSG_GL3_AVAILABLE)

        IF ( QT4_FOUND OR Qt5Widgets_FOUND)
            ADD_SUBDIRECTORY(osgviewerQt)
            ADD_SUBDIRECTORY(osgqfont)
        ENDIF()

        IF ( (QT4_FOUND AND QT_QTWEBKIT_FOUND) OR Qt5WebKitWidgets_FOUND )
            ADD_SUBDIRECTORY(osgQtWidgets)
            ADD_SUBDIRECTORY(osgQtBrowser)
        ENDIF()

    ENDIF()

ENDIF()

