# timeit

C/C++ macro for timing line/lines of code easily, this marco doesn't need to create a lambda to test code. Also it doesn't broken the context of your code, it just insert timing code automatically. The use of `__COUNTER__` may create unique variable name automatically, but the risk of naming conflicts still exists, please use with caution. And this macro can be easily disabled by defining `DISABLE_TIMEIT`.


# examples
## single line timing 
```cpp
#include <timeit.h>
#include <Eigen/Eigen> // e.g. use some thirdparty lib

TIMEIT("create a quaternion",  Eigen::Quaternion<double> q(2,0,1,-3);)
```

## multi line timing 
```cpp
#include <timeit.h>
#include <Eigen/Eigen> // e.g. use some thirdparty lib

TIMEIT("create a quaternion and normalize it",  
Eigen::Quaternion<double> q(2,0,1,-3);
q.normalize();)
```

## nested timing
```cpp
#include <timeit.h>
#include <Eigen/Eigen> // e.g. use some thirdparty lib

TIMEIT("create a quaternion and normalize it",  
TIMEIT("create a quaternion",  Eigen::Quaternion<double> q(2,0,1,-3);)
TIMEIT("normalize a quaternion", q.normalize();)
)
```

## disable timeit
```cpp
#define DISABLE_TIMEIT
#include <timeit.h>
```