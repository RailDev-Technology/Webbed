cmake_minimum_required(VERSION 3.0)

project(webbed)

include(FeatureSummary)

################# set KDE specific information #################
find_package(ECM 0.0.8 REQUIRED NO_MODULE)

# where to look first for cmake modules, before ${CMAKE_ROOT}/Modules/ is checked
set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} ${ECM_MODULE_PATH})

include(KDEInstallDirs)
include(KDECMakeSettings)
include(KDECompilerSettings NO_POLICY_SCOPE)
include(ECMSetupVersion)
include(ECMGenerateHeaders)
include(ECMPoQmTools)

################# Find dependencies #################
find_package(Qt5 REQUIRED COMPONENTS Core Gui Qml QuickControls2 Svg)
find_package(KF5Kirigami2)
find_package(KF5I18n)

################# Enable C++11 features for clang and gcc #################
set(CMAKE_CXX_STANDARD 11)

################# build and install #################
add_subdirectory(src)

install(PROGRAMS tech.raildev.webbed.desktop DESTINATION ${KDE_INSTALL_APPDIR})
install(FILES tech.raildev.webbed.appdata.xml DESTINATION ${KDE_INSTALL_METAINFODIR})

feature_summary(WHAT ALL INCLUDE_QUIET_PACKAGES FATAL_ON_MISSING_REQUIRED_PACKAGES)
