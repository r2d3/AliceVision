# Headers
set(colorHarmonization_files_headers
  CommonDataByPair.hpp
  CommonDataByPair_fullFrame.hpp
  CommonDataByPair_matchedPoints.hpp
  CommonDataByPair_vldSegment.hpp
  GainOffsetConstraintBuilder.hpp
)

# Sources
set(colorHarmonization_files_sources
  GainOffsetConstraintBuilder.cpp
)

# Tests
set(colorHarmonization_files_test
  gainOffsetConstraintBuilder_test.cpp
)

add_library(aliceVision_colorHarmonization
  ${colorHarmonization_files_headers}
  ${colorHarmonization_files_sources}
)

target_link_libraries(aliceVision_colorHarmonization
  INTERFACE aliceVision_image
            ${CLP_LIBRARIES}
            ${COINUTILS_LIBRARY}
            ${OSI_LIBRARY}
            ${LOG_LIB}
)

install(TARGETS aliceVision_colorHarmonization
  DESTINATION lib/
  EXPORT aliceVision-targets
)

UNIT_TEST(aliceVision gainOffsetConstraintBuilder "aliceVision_colorHarmonization")

add_custom_target(aliceVision_colorHarmonization_ide SOURCES ${colorHarmonization_files_headers} ${colorHarmonization_files_test})
