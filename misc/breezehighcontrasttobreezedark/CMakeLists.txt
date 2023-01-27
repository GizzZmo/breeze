find_package(KF6ConfigWidgets ${KF6_MIN_VERSION} REQUIRED)

add_executable(breezehighcontrasttobreezedark main.cpp)

target_link_libraries(breezehighcontrasttobreezedark KF6::ConfigWidgets)

install(TARGETS breezehighcontrasttobreezedark DESTINATION ${KDE_INSTALL_LIBDIR}/kconf_update_bin/)
install(FILES breezehighcontrasttobreezedark.upd DESTINATION ${KDE_INSTALL_KCONFUPDATEDIR})
