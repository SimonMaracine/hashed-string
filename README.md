# hashed-string

A small header-only utility library handling constexpr hashed strings.

Simply copy the header file and integrate it into your build system however you want. Note the license.

```cpp
#include <print>
#include <unordered_map>

#include "hashed_string.hpp"

using namespace hashed_string::literals;

int main() {
    static constexpr auto h1 = hashed_string::HashedStr32();
    static constexpr auto h2 = hashed_string::HashedStr32("some_string");
    static constexpr auto h3 = "some_other_string"_h;
    const auto h4 = hashed_string::HashedStr32(std::string("dynamic_string"));

    std::println("{}", h1);
    std::println("{}", h2);
    std::println("{}", h3);
    std::println("{}", h4);

    std::unordered_map<hashed_string::HashedStr64, int, hashed_string::StrHash<hashed_string::HashedStr64>> map;
    map["one"_H] = 1;
    map["two"_H] = 2;
    map["three"_H] = 3;
}
```
