# --------------------------------------------------------------
#  bit
#
#  provides:
#    bit.lua
#    bit/vendor.so
# --------------------------------------------------------------
set(MODULE_NAME bit)

# --------------------------------------------------------------
#  module
# --------------------------------------------------------------
add_custom_target(${MODULE_NAME} true)

# --------------------------------------------------------------
#  bit_vendor
# --------------------------------------------------------------
set(target "${MODULE_NAME}_vendor")

add_library(${target} MODULE vendor/bit.c)
set_target_properties(${target}
  PROPERTIES OUTPUT_NAME vendor
  LINK_FLAGS ${PLAT_OBJ_FLAGS}
  PREFIX ""
  SUFFIX ".so"
)  
add_dependencies(${MODULE_NAME} ${target})

# --------------------------------------------------------------
#  install bit/vendor.so
# --------------------------------------------------------------
install(TARGETS ${target}
  DESTINATION ${LUBYK_LIB}/lib/${MODULE_NAME}
)


# --------------------------------------------------------------
#  install bit.lua
# --------------------------------------------------------------
install(DIRECTORY lib
  DESTINATION ${LUBYK_LIB}
)

