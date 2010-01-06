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
else(WIN32)
    set(SRCS_PLATFORM Posix/SignalTranslator.cpp Posix/TimeHelpers.cpp)
    set(INCLUDE_PLATFORM ${UNITTEST_CPP_SOURCE_DIR}/include/Posix)
endif(WIN32)

# List the include paths
include_directories(${UNITTEST_CPP_SOURCE_DIR}/include ${INCLUDE_PLATFORM})

# Declaration of the library
add_library(UnitTest++ STATIC ${SRCS} ${SRCS_PLATFORM})
