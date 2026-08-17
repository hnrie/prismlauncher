cmake_minimum_required(VERSION 3.15)
project(launcher Java)
find_package(Java 1.7 REQUIRED COMPONENTS Development)

include(UseJava)
set(CMAKE_JAVA_JAR_ENTRY_POINT org.vinilauncher.EntryPoint)
set(CMAKE_JAVA_COMPILE_FLAGS -target 7 -source 7)

set(SRC
    org/vinilauncher/EntryPoint.java
    org/vinilauncher/launcher/Launcher.java
    org/vinilauncher/launcher/impl/AbstractLauncher.java
    org/vinilauncher/launcher/impl/StandardLauncher.java
    org/vinilauncher/exception/ParameterNotFoundException.java
    org/vinilauncher/exception/ParseException.java
    org/vinilauncher/utils/Parameters.java
    org/vinilauncher/utils/ReflectionUtils.java
    org/vinilauncher/utils/logging/Level.java
    org/vinilauncher/utils/logging/Log.java
    org/vinilauncher/legacy/LegacyProxy.java
)

set(LEGACY_SRC
    legacy/org/vinilauncher/legacy/LegacyFrame.java
    legacy/org/vinilauncher/legacy/LegacyLauncher.java
    legacy/org/vinilauncher/legacy/fix/online/Handler.java
    legacy/org/vinilauncher/legacy/fix/online/OnlineFixes.java
    legacy/org/vinilauncher/legacy/fix/online/OnlineModeFix.java
    legacy/org/vinilauncher/legacy/fix/online/SkinFix.java
    legacy/org/vinilauncher/legacy/utils/Base64.java
    legacy/org/vinilauncher/legacy/utils/api/MojangApi.java
    legacy/org/vinilauncher/legacy/utils/api/Texture.java
    legacy/org/vinilauncher/legacy/utils/json/JsonParseException.java
    legacy/org/vinilauncher/legacy/utils/json/JsonParser.java
    legacy/org/vinilauncher/legacy/utils/url/ByteArrayUrlConnection.java
    legacy/org/vinilauncher/legacy/utils/url/UrlUtils.java
    legacy/net/minecraft/Launcher.java
    legacy/org/vinilauncher/legacy/LegacyProxy.java
)

add_jar(NewLaunch ${SRC})
add_jar(NewLaunchLegacy ${LEGACY_SRC} INCLUDE_JARS NewLaunch)
install_jar(NewLaunch "${JARS_DEST_DIR}")
install_jar(NewLaunchLegacy "${JARS_DEST_DIR}")
