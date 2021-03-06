SET(SOURCE_FILES 
	${KLAYGE_PROJECT_DIR}/Tools/src/KGEditor/KGEditorCore/KGEditorCore.cpp
)

SET(HEADER_FILES
	${KLAYGE_PROJECT_DIR}/Tools/src/KGEditor/KGEditorCore/Common.hpp
	${KLAYGE_PROJECT_DIR}/Tools/src/KGEditor/KGEditorCore/KGEditorCore.hpp
	${KLAYGE_PROJECT_DIR}/Tools/src/KGEditor/KGEditorCore/PreDeclare.hpp
)

SET(EFFECT_FILES
	${KLAYGE_PROJECT_DIR}/Tools/media/KGEditor/MVUtil.fxml
)

SOURCE_GROUP("Source Files" FILES ${SOURCE_FILES})
SOURCE_GROUP("Header Files" FILES ${HEADER_FILES})
SOURCE_GROUP("Resource Files" FILES ${RESOURCE_FILES})
SOURCE_GROUP("Effect Files" FILES ${EFFECT_FILES})
SOURCE_GROUP("Post Processors" FILES ${POST_PROCESSORS})
SOURCE_GROUP("UI Files" FILES ${UI_FILES})

SET(KGEDITOR_CORE_NAME KGEditorCore)

ADD_LIBRARY(${KGEDITOR_CORE_NAME} SHARED ${SOURCE_FILES} ${HEADER_FILES} ${RESOURCE_FILES} ${EFFECT_FILES} ${POST_PROCESSORS} ${UI_FILES})

target_compile_definitions(${KGEDITOR_CORE_NAME}
	PRIVATE
		-DKLAYGE_KGEDITOR_CORE_SOURCE
)

ADD_DEPENDENCIES(${KGEDITOR_CORE_NAME} AllInEngine)

SET_TARGET_PROPERTIES(${KGEDITOR_CORE_NAME} PROPERTIES
	ARCHIVE_OUTPUT_DIRECTORY ${KLAYGE_TOOLS_LIB_OUTPUT_DIR}
	ARCHIVE_OUTPUT_DIRECTORY_DEBUG ${KLAYGE_TOOLS_LIB_OUTPUT_DIR}
	ARCHIVE_OUTPUT_DIRECTORY_RELEASE ${KLAYGE_TOOLS_LIB_OUTPUT_DIR}
	ARCHIVE_OUTPUT_DIRECTORY_RELWITHDEBINFO ${KLAYGE_TOOLS_LIB_OUTPUT_DIR}
	ARCHIVE_OUTPUT_DIRECTORY_MINSIZEREL ${KLAYGE_TOOLS_LIB_OUTPUT_DIR}
	RUNTIME_OUTPUT_DIRECTORY ${KLAYGE_BIN_DIR}
	RUNTIME_OUTPUT_DIRECTORY_DEBUG ${KLAYGE_BIN_DIR}
	RUNTIME_OUTPUT_DIRECTORY_RELEASE ${KLAYGE_BIN_DIR}
	RUNTIME_OUTPUT_DIRECTORY_RELWITHDEBINFO ${KLAYGE_BIN_DIR}
	RUNTIME_OUTPUT_DIRECTORY_MINSIZEREL ${KLAYGE_BIN_DIR}
	LIBRARY_OUTPUT_DIRECTORY ${KLAYGE_BIN_DIR}
	LIBRARY_OUTPUT_DIRECTORY_DEBUG ${KLAYGE_BIN_DIR}
	LIBRARY_OUTPUT_DIRECTORY_RELEASE ${KLAYGE_BIN_DIR}
	LIBRARY_OUTPUT_DIRECTORY_RELWITHDEBINFO ${KLAYGE_BIN_DIR}
	LIBRARY_OUTPUT_DIRECTORY_MINSIZEREL ${KLAYGE_BIN_DIR}
	PROJECT_LABEL ${KGEDITOR_CORE_NAME}
	DEBUG_POSTFIX ${CMAKE_DEBUG_POSTFIX}
	OUTPUT_NAME ${KGEDITOR_CORE_NAME}
	FOLDER "KlayGE/Tools/KGEditor"
)

target_link_libraries(${KGEDITOR_CORE_NAME}
	PUBLIC
		${KLAYGE_CORELIB_NAME}
)
