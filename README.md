# rollup-plugin-c
allows you to compose c or any code into modules defined as rollup bundle also includes a lot of modules to create modules

## Why?
This is part of rollup-plugin-generate-v8-runtime it gets used to unifie the build process of v8 c, c++ components but can be used standalone to bundle modular c code in fact this also includes rollup-plugin-c-make which implements gcc, llvm cmake, 


```js
import my,{ anySymbol } from 'my.cc'; // will include headers
import v8 from 'libv8_monolithic.cc'; // will include headers
import anyModule from 'protocol:anyWhere'


// will use gcc by default at present 
const build = { "libv8.so": v8, "my.so": my, "something.so": anySymbol, anyModule };
// will when executed with rollup plugin c produce the files as bundel so that you can reuse that or write it out to disk. 
```


## Usage

```js
import RollupPluginC from '@rollup/plugin-c';

const rollupGcc = RollupPluginC({ C: "gcc" }) // linkerflags etc if they can not get guessed by eg RollupPluginC.resolve('.cc .c .S Makefile .h')

const build = rollupGcc({}); // Returns references to the files as also the binary files it self to write them out if you supply a write Task directly it will write them out to disk as Stream as a Task is a Stream.
```
