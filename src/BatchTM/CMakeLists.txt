SET(FILES_UI
${CMAKE_CURRENT_SOURCE_DIR}/BatchTMDialog.ui)
SET(FILES_H
${CMAKE_CURRENT_SOURCE_DIR}/BatchTMDialog.h
${CMAKE_CURRENT_SOURCE_DIR}/BatchTMJob.h)
SET(FILES_CPP
${CMAKE_CURRENT_SOURCE_DIR}/BatchTMDialog.cpp
${CMAKE_CURRENT_SOURCE_DIR}/BatchTMJob.cpp)

INCLUDE_DIRECTORIES(${CMAKE_CURRENT_BINARY_DIR})

QT5_WRAP_CPP(FILES_MOC ${FILES_H})
QT5_WRAP_UI(FILES_UI_H ${FILES_UI})

ADD_LIBRARY(batchtm STATIC ${FILES_H} ${FILES_CPP} ${FILES_MOC} ${FILES_UI_H})
TARGET_LINK_LIBRARIES(batchtm Qt5::Core Qt5::Gui Qt5::Widgets Qt5::Sql Qt5::Xml)

SET(FILES_TO_TRANSLATE ${FILES_TO_TRANSLATE} ${FILES_CPP} ${FILES_H} ${FILES_UI} PARENT_SCOPE)
SET(LUMINANCE_MODULES_GUI ${LUMINANCE_MODULES_GUI} batchtm PARENT_SCOPE)
