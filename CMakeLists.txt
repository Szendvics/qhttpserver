cmake_minimum_required(VERSION 3.1)

# === PROJECT ==============================================================
include(cmakeTargets)
project(QHttpServer CXX)

# === CONFIG ===============================================================
set(PublicHeaderSubDirName libfins)

set(PublicHeaderLocation       "${CMAKE_CURRENT_SOURCE_DIR}/QHttpServer")
set(HeaderLocation             "${CMAKE_CURRENT_SOURCE_DIR}/http-parser")
set(SourceLocation             "${CMAKE_CURRENT_SOURCE_DIR}/QHttpServer")


# === DEPS =================================================================
set(PublicHeaders
    ${PublicHeaderLocation}/qhttpconnection.h
    ${PublicHeaderLocation}/qhttprequest.h
    ${PublicHeaderLocation}/qhttpresponse.h
    ${PublicHeaderLocation}/qhttpserver.h
    ${PublicHeaderLocation}/qhttpserverapi.h
    ${PublicHeaderLocation}/qhttpserverfwd.h
    ${HeaderLocation}/http_parser.h
)

set(Headers

)

set(Sources
    ${SourceLocation}/qhttpconnection.cpp
    ${SourceLocation}/qhttprequest.cpp
    ${SourceLocation}/qhttpresponse.cpp
    ${SourceLocation}/qhttpserver.cpp
    ${SourceLocation}/../http-parser/http_parser.c
)


set(LinkLibraries

)


set(FindPackages

)


set(QtComponents
    Core
    Network
)

set(OtherFiles

)


find_package(Qt5 COMPONENTS Core REQUIRED)
AddLibraryTarget(
    TargetName              ${PROJECT_NAME}

    PublicIncludeLocation   ${PublicHeaderLocation}
    IncludeLocation         ${HeaderLocation}
    SourceLocation          ${SourceLocation}

    LibMode                 STATIC

    PublicHeaders           ${PublicHeaders}
    Headers                 ${Headers}
    Sources                 ${Sources}

    LinkLibraries           ${LinkLibraries}
    FindPackages            ${FindPackages}
    QtComponents            ${QtComponents}

    OtherFiles              ${OtherFiles}

    #options
    RemoveLibPrefix
    QtProject
    GenerateBuildInfo
)
