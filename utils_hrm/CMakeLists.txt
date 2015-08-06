INCLUDE_DIRECTORIES(${PROJECT_SOURCE_DIR}/src ${GNULIBS_INCLUDE_DIR})
LINK_LIBRARIES(${PROJECT_NAME} ${REQUIRED_LIBRARIES} )

ADD_EXECUTABLE(aruco_hrm_create_dictionary aruco_hrm_create_dictionary.cpp)
ADD_EXECUTABLE(aruco_hrm_test aruco_hrm_test.cpp)
ADD_EXECUTABLE(aruco_hrm_create_board aruco_hrm_create_board.cpp)
ADD_EXECUTABLE(aruco_hrm_test_board aruco_hrm_test_board.cpp)

# Postfix of EXEs:
if(WIN32)
  set(ARUCO_DEBUG_POSTFIX _d)
endif()
if(DEFINED CMAKE_DEBUG_POSTFIX)
  set(ARUCO_DEBUG_POSTFIX "${CMAKE_DEBUG_POSTFIX}")
endif()
set_target_properties(aruco_hrm_create_dictionary PROPERTIES DEBUG_POSTFIX "${ARUCO_DEBUG_POSTFIX}")
set_target_properties(aruco_hrm_test PROPERTIES DEBUG_POSTFIX "${ARUCO_DEBUG_POSTFIX}")
set_target_properties(aruco_hrm_create_board PROPERTIES DEBUG_POSTFIX "${ARUCO_DEBUG_POSTFIX}")
set_target_properties(aruco_hrm_test_board PROPERTIES DEBUG_POSTFIX "${ARUCO_DEBUG_POSTFIX}")

INSTALL(TARGETS aruco_hrm_create_dictionary aruco_hrm_test aruco_hrm_create_board aruco_hrm_test_board RUNTIME DESTINATION bin)

