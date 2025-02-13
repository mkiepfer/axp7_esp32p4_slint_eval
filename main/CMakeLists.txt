idf_component_register(
    SRCS "slint-hello-world.cpp"
    INCLUDE_DIRS "."
    REQUIRES slint
)

slint_target_sources(${COMPONENT_LIB} ui/axp7_window.slint)