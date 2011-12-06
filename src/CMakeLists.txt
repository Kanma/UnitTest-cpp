# List the source files
set(SRCS AssertException.cpp
         Checks.cpp
         CurrentTest.cpp
         DeferredTestReporter.cpp
         DeferredTestResult.cpp
         MemoryOutStream.cpp
         ReportAssert.cpp
         Test.cpp
         TestDetails.cpp
         TestList.cpp
         TestReporter.cpp
         TestReporterStdout.cpp
         TestResults.cpp
         TestRunner.cpp
         TimeConstraint.cpp
         XmlTestReporter.cpp
)


# List the plateform-specific source files
if (WIN32)
    set(SRCS_PLATFORM Win32/TimeHelpers.cpp)
    set(INCLUDE_PLATFORM ${UNITTEST_CPP_SOURCE_DIR}/include/Win32)
else()
    set(SRCS_PLATFORM Posix/SignalTranslator.cpp Posix/TimeHelpers.cpp)
    set(INCLUDE_PLATFORM ${UNITTEST_CPP_SOURCE_DIR}/include/Posix)
endif()


# List the include paths
set(INCLUDE_PATHS "${UNITTEST_CPP_SOURCE_DIR}/include")

include_directories(${INCLUDE_PATHS} ${INCLUDE_PLATFORM})


# Declaration of the library
xmake_create_static_library(UNITTEST_CPP UnitTest++ ${SRCS} ${SRCS_PLATFORM})

if (WIN32)
    # Disable some warnings in Visual Studio
    xmake_add_to_property(UNITTEST_CPP COMPILE_DEFINITIONS "_CRT_SECURE_NO_WARNINGS")
endif()


# Exportations
xmake_export_include_paths(UNITTEST_CPP ${INCLUDE_PATHS})
