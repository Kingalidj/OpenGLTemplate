set(IMGUI_DIR ${CMAKE_CURRENT_SOURCE_DIR}/imgui)
set(GLAD_DIR ${CMAKE_CURRENT_SOURCE_DIR}/glad)
set(GLFW_DIR ${CMAKE_CURRENT_SOURCE_DIR}/glfw)

# == glad ==

add_library(glad STATIC)

target_sources( glad
	PRIVATE ${GLAD_DIR}/src/glad.c
	)

target_include_directories( glad
	PUBLIC ${GLAD_DIR}/include
	)

# == glfw ==

add_subdirectory(glfw)
include_directories(glfw/include)

# == imgui ==

add_library(imgui STATIC)

target_sources( imgui
	PRIVATE
	${IMGUI_DIR}/imgui_demo.cpp
	${IMGUI_DIR}/imgui_draw.cpp
	${IMGUI_DIR}/imgui_tables.cpp
	${IMGUI_DIR}/imgui_widgets.cpp
	${IMGUI_DIR}/imgui.cpp

	PRIVATE
	${IMGUI_DIR}/backends/imgui_impl_opengl3.cpp
	${IMGUI_DIR}/backends/imgui_impl_glfw.cpp
	)

target_include_directories( imgui
	PUBLIC ${IMGUI_DIR}
	PUBLIC ${IMGUI_DIR}/backends
	)


target_link_libraries(imgui PUBLIC glfw)

