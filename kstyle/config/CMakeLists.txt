### configuration plugin
add_definitions(-DTRANSLATION_DOMAIN=\"breeze_style_config\")
set(kstyle_breeze_config_PART_SRCS breezestyleconfig.cpp)

set(kstyle_breeze_config_PART_SRCS ${kstyle_breeze_config_PART_SRCS} breezestyleconfigmodule.cpp)

kconfig_add_kcfg_files(kstyle_breeze_config_PART_SRCS ../breezestyleconfigdata.kcfgc)
set(kstyle_breeze_config_PART_FORMS ui/breezestyleconfig.ui)
ki18n_wrap_ui(kstyle_breeze_config_PART_FORMS_HEADERS ${kstyle_breeze_config_PART_FORMS})

kcoreaddons_add_plugin(breezestyleconfig SOURCES
    ${kstyle_breeze_config_PART_SRCS}
    ${kstyle_breeze_config_PART_FORMS_HEADERS}
    INSTALL_NAMESPACE "plasma/kcms/systemsettings_qwidgets"
)

target_link_libraries(breezestyleconfig Qt::Core Qt::Gui Qt::Widgets Qt::DBus)
target_link_libraries(breezestyleconfig KF6::CoreAddons KF6::ConfigCore KF6::ConfigWidgets KF6::I18n)
kcmutils_generate_desktop_file(breezestyleconfig)

set(breeze_settings_SOURCES main.cpp)
add_executable(breeze-settings6 ${breeze_settings_SOURCES} )
target_link_libraries(breeze-settings6 Qt::Core Qt::Gui Qt::Widgets )
target_link_libraries(breeze-settings6 KF6::I18n KF6::KCMUtils KF6::CoreAddons)

install(TARGETS breeze-settings6 ${KDE_INSTALL_TARGETS_DEFAULT_ARGS})

# icon
ecm_install_icons(ICONS sc-apps-breeze-settings.svgz
    DESTINATION ${KDE_INSTALL_ICONDIR}
    THEME hicolor )
