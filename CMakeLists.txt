cmake_minimum_required(VERSION 3.10)

project(wboard LANGUAGES CXX VERSION 1.0)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_AUTOUIC ON)

find_package(QT NAMES Qt6 REQUIRED COMPONENTS Widgets WebEngine Network)
find_package(Qt${QT_VERSION_MAJOR} REQUIRED COMPONENTS Widgets WebEngine Network)

aux_source_directory(${PROJECT_SOURCE_DIR}/Source/adaptors adaptors_src)
aux_source_directory(${PROJECT_SOURCE_DIR}/Source/api api_src)
aux_source_directory(${PROJECT_SOURCE_DIR}/Source/core core_src)
aux_source_directory(${PROJECT_SOURCE_DIR}/Source/customWidgets customWidgets_src)
aux_source_directory(${PROJECT_SOURCE_DIR}/Source/desktop desktop_src)
aux_source_directory(${PROJECT_SOURCE_DIR}/Source/document document_src)
aux_source_directory(${PROJECT_SOURCE_DIR}/Source/domain domain_src)
aux_source_directory(${PROJECT_SOURCE_DIR}/Source/frameworks frameworks_src)
aux_source_directory(${PROJECT_SOURCE_DIR}/Source/globals globals_src)
aux_source_directory(${PROJECT_SOURCE_DIR}/Source/gui gui_src)
aux_source_directory(${PROJECT_SOURCE_DIR}/Source/network network_src)
aux_source_directory(${PROJECT_SOURCE_DIR}/Source/pdf pdf_src)
aux_source_directory(${PROJECT_SOURCE_DIR}/Source/pdf-merger pdf-merger_src)
aux_source_directory(${PROJECT_SOURCE_DIR}/Source/podcast podcast_src)
aux_source_directory(${PROJECT_SOURCE_DIR}/Source/qtsingleapplication qtsingleapplication_src)
aux_source_directory(${PROJECT_SOURCE_DIR}/Source/tools tools_src)
aux_source_directory(${PROJECT_SOURCE_DIR}/Source/web web_src)

qt_add_executable(${PROJECT_NAME} 
    ${adaptors_src}
    ${api_src}
    ${core_src}
    ${customWidgets_src}
    ${desktop_src}
    ${document_src}
    ${domain_src}
    ${frameworks_src}
    ${globals_src}
    ${gui_src}
    ${network_src}
    ${pdf_src}
    ${pdf-merger_src}
    ${podcast_src}
    ${qtsingleapplication_src}
    ${tools_src}
    ${web_src}
)



target_link_libraries(${PROJECT_NAME} PRIVATE Qt${QT_VERSION_MAJOR}::Widgets Qt${QT_VERSION_MAJOR}::WebEngine)
# target_link_libraries(${PROJECT_NAME} PRIVATE ${PROJECT_SOURCE_DIR}/ThirdParty/openssl/lib)
target_link_libraries(${PROJECT_NAME} PRIVATE ${PROJECT_SOURCE_DIR}/ThirdParty/quazip/Debug/bin/quazip)

target_include_directories(${PROJECT_NAME} PRIVATE ${PROJECT_SOURCE_DIR}/Source)
target_include_directories(${PROJECT_NAME} PRIVATE ${PROJECT_SOURCE_DIR}/ThirdParty/openssl/include)
target_include_directories(${PROJECT_NAME} PRIVATE ${PROJECT_SOURCE_DIR}/ThirdParty/quazip/include)