

According to the source code, the maximum size of a list is PY_SSIZE_T_MAX/sizeof(PyObject*). PY_SSIZE_T_MAX is defined in pyport.h to be ((size_t) -1)>>1 On a regular 32bit system, this is (4294967295 / 2) / 4 or 536870912. Therefore the maximum size of a python list on a 32 bit system is 536,870,912 elements. As long as the number of elements you have is equal or below this, all list functions should operate correctly.


On a regular 32bit system, this is (4294967295 / 2) / 4 or 536870912.

Therefore the maximum size of a python list on a 32 bit system is 536,870,912 elements.
