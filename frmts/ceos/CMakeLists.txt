add_gdal_driver(TARGET gdal_CEOS SOURCES ceosopen.h ceosdataset.cpp ceosopen.c PLUGIN_CAPABLE NO_DEPS)
gdal_standard_includes(gdal_CEOS)

if (NOT GDAL_ENABLE_DRIVER_CEOS_PLUGIN)
  add_executable(ceostest EXCLUDE_FROM_ALL ceostest.c)
  target_include_directories(ceostest PRIVATE $<TARGET_PROPERTY:gdal_CEOS,SOURCE_DIR>)
  target_link_libraries(ceostest PRIVATE $<TARGET_NAME:${GDAL_LIB_TARGET_NAME}> gdal_CEOS)
endif ()
