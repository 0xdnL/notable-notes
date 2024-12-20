---
tags: [lua]
title: lua
created: '2020-09-02T12:55:03.179Z'
modified: '2024-12-04T15:52:50.317Z'
---

# lua

> lightweight, high-level, multi-paradigm programming language designed primarily for embedded use in applications

- uses "mechanisms over policies"
- designed to be embedded/integrated with software written in `c` and other conventional languages

## install

```sh
apt install build-essential libreadline-dev

curl -R -O http://www.lua.org/ftp/lua-${VERSION}.tar.gz
tar -zxf lua-${VERSION}.tar.gz && cd lua-${VERSION}
make linux test && make install
```

## usage

```sh
lua               # standalone interpreter and repl

lua hello.lua     # run script
```

## comments

```lua
-- this is a comment

--[[ this is a
     multiline comment
--]]
```

## variables: simple literals

```lua
local number = 9

local string = "hello, world"
local single = 'works also'
local multi = [[ this is
 a multiline and literal]]

local truth, lies = true, false

local nothing = nil
```


## functions

> are firstclass

```lua
local function hello(name)
    print("hello: ", name)
end

local greet = function(name)
    -- .. <- concats strings
    print("greetings, " .. name .. "!")
end


-- higher order function: function that returns other function
local higher_order = function(value)
    return funtion(another)
        return value + another
    end
end

local add_one = higher_order(1)
print("add_one(2): ", add_one(2))


-- Create a prototype object
local person = {
  name = "John",
  age = 30,
  sayHello = function(self)
    print("Hello, my name is " .. self.name)
  end
}

-- Create a new object that inherits from the prototype
local student = {
  studentID = "12345"
}
setmetatable(student, {__index = person})

-- Use the inherited properties and methods
print(student.name)
print(student.age)
student:sayHello()
```


## variables: tables

> effecitvely lua's only data struct

```lua
local list = { "first", 2, false, function() print("fourth") end }
print("index starts at 1:", list[1])
print("fourth is 4......:", list[4]())

local map = {
    literal_key = "some string"      -- map.literal_key
    ["an expression"] = "works too"  -- t["an expression"]
    [function() end] = true          -- t[function() end]
}
```

## see also

- [[nvchad]]
- [[luac]]
- [[luarocks]]
- [[nginx]]
- [[javascript]]
- [[tcl]]
- [[awk]]
- [[groovy]]
- [lua.org/pil/contents.html](https://www.lua.org/pil/contents.html)
- [Learn Lua in 15 Minutes (2013) | Hacker News](https://news.ycombinator.com/item?id=23694667)
