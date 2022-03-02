 
```
 bazel build //src:a 
INFO: Analyzed target //src:a (0 packages loaded, 0 targets configured).
INFO: Found 1 target...
Target //src:a up-to-date:
  bazel-bin/src/a.d.ts
INFO: Elapsed time: 0.094s, Critical Path: 0.00s
INFO: 1 process: 1 internal.
INFO: Build completed successfully, 1 total action


```

```
 bazel build //...
 
INFO: Analyzed 9 targets (2 packages loaded, 3 targets configured).
INFO: Found 9 targets...
INFO: Elapsed time: 0.151s, Critical Path: 0.00s
INFO: 1 process: 1 internal.
INFO: Build completed successfully, 1 total action

```


```
bazel test --test_output=errors  //...

 Test output for //src:test:
 FAIL  src/b.test.js
  ● Test suite failed to run

    Cannot find module './a' from 'src/b.js'

    Require stack:
      src/b.js
      src/b.test.js


    However, Jest was able to find:
        './a.d.ts'

    You might want to include a file extension in your import, or update your 'moduleFileExtensions', which is currently ['js', 'jsx', 'ts', 'tsx', 'json', 'node'].

    See https://jestjs.io/docs/configuration#modulefileextensions-arraystring

      2 | Object.defineProperty(exports, "__esModule", { value: true });
      3 | const tslib_1 = require("tslib");
    > 4 | const a_1 = tslib_1.__importDefault(require("./a"));
        |                                     ^
      5 | exports.default = a_1.default;
      6 |

      at Resolver.resolveModule (../npm/node_modules/jest-resolve/build/resolver.js:324:11)
      at Object.require (src/b.js:4:37)

Test Suites: 1 failed, 1 total
Tests:       0 total
Snapshots:   0 total
Time:        0.213 s
Ran all test suites.
```
