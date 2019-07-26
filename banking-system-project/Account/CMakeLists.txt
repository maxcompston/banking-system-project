add_library (Account SHARED
  Account.h
  Account.cpp)

install (TARGETS Account DESTINATION bin)
install (FILES Account.h DESTINATION include)
