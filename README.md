# Demonstration of a bug in Android Gradle Plugin when CMake defines an object library

This project demonstrates [bug 134374003](https://issuetracker.google.com/issues/134374003).

It seems Android Gradle Plugin treats object libraries defined in CMakeLists when linked to with `target_link_libraries`
as if they were shared libraries and therefore as default targets for compilation. This leads to compilation failure:
> Expected output file at … for target … but there was none

For a workaround, specify all targets explicitely (uncomment [line 17 in app's build.gradle](app/build.gradle#L17)) or
use `$<TARGET_OBJECTS:…>`; however the latter does not propagate compiler and linker flags from the object library.
