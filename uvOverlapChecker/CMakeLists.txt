project(findUvOverlaps CXX)

add_maya_library(NAME ${PROJECT_NAME}
        PRIVATE_SOURCE
        src/findUvOverlaps.cpp
        src/findUvOverlaps.h
        src/bentleyOttmann/bentleyOttmann.cpp
        src/bentleyOttmann/bentleyOttmann.hpp
        src/bentleyOttmann/event.hpp
        src/bentleyOttmann/event.cpp
        src/bentleyOttmann/lineSegment.hpp
        src/bentleyOttmann/lineSegment.cpp
        src/bentleyOttmann/point2D.hpp
        src/bentleyOttmann/point2D.cpp
        src/bentleyOttmann/vector2D.hpp
        src/bentleyOttmann/vector2D.cpp
        )

if (NOT APPLE)
    find_package(OpenMP REQUIRED)
    target_link_libraries(
        ${PROJECT_NAME}
        PRIVATE
        OpenMP::OpenMP_CXX
    )
endif()

install(TARGETS ${PROJECT_NAME} DESTINATION plug-ins)
