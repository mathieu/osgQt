IF ( Qt5Widgets_FOUND )
    include(GenerateExportHeader)

    SET(LIB_NAME osgQOpenGL)
    SET(HEADER_INSTALL_DIR osgQOpenGL)

    set(CMAKE_INCLUDE_CURRENT_DIR yes)

    SET(HEADER_PATH ${OpenSceneGraph_SOURCE_DIR}/include/osgQOpenGL)

    SET(SOURCE_H 
        ${HEADER_PATH}/osgQOpenGLWidget
        ${HEADER_PATH}/osgQOpenGLWindow
        ${HEADER_PATH}/OSGRenderer
    )

#[[    foreach(header ${SOURCE_H})
        set(MOC_OPTIONS "${MOC_OPTIONS} -f${header}")
    endforeach(header)
]]
    qt5_wrap_cpp(SOURCES_H_MOC ${SOURCE_H} #[[OPTIONS ${MOC_OPTIONS}]])

    SET(TARGET_H
        ${SOURCE_H}
        ${HEADER_PATH}/CullVisitorEx
        ${HEADER_PATH}/GraphicsWindowEx
        ${HEADER_PATH}/RenderStageEx
        ${HEADER_PATH}/StateEx
        ${CMAKE_CURRENT_BINARY_DIR}/osgQOpenGL/Export
    )


    SET(TARGET_SRC
        CullVisitorEx.cpp
        GraphicsWindowEx.cpp
        osgQOpenGLWidget.cpp
        osgQOpenGLWindow.cpp
        OSGRenderer.cpp
        RenderStageEx.cpp
        StateEx.cpp
        ${SOURCES_H_MOC}
        ${OPENSCENEGRAPH_VERSIONINFO_RC}
    )

    SET(TARGET_LIBRARIES  ${OPENSCENEGRAPH_LIBRARIES})

    SETUP_LIBRARY(${LIB_NAME})

	generate_export_header(${LIB_NAME} EXPORT_FILE_NAME "osgQOpenGL/Export")
	
    target_link_libraries(${LIB_NAME} Qt5::Widgets Qt5::OpenGL)
ENDIF()