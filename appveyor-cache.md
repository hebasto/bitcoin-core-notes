AppVeyor CI
===========

Cleaning up cache
-----------------

### Symptoms

The log excerpt:

```
...
LINK : fatal error C1047: The object or library file 'c:\tools\vcpkg\installed\x64-windows-static\lib\libzmq-mt-s-4_3_3.lib' was created with an older compiler than other objects; rebuild old objects and libraries [C:\projects\bitcoin\build_msvc\bitcoind\bitcoind.vcxproj]
LINK : fatal error LNK1257: code generation failed [C:\projects\bitcoin\build_msvc\bitcoind\bitcoind.vcxproj]
LINK : fatal error C1047: The object or library file 'c:\tools\vcpkg\installed\x64-windows-static\lib\libzmq-mt-s-4_3_3.lib' was created with an older compiler than other objects; rebuild old objects and libraries [C:\projects\bitcoin\build_msvc\bench_bitcoin\bench_bitcoin.vcxproj]
LINK : fatal error LNK1257: code generation failed [C:\projects\bitcoin\build_msvc\bench_bitcoin\bench_bitcoin.vcxproj]
LINK : fatal error C1047: The object or library file 'C:\Qt5.9.8_x64_static_vs2019\lib\Qt5Core.lib' was created with an older compiler than other objects; rebuild old objects and libraries [C:\projects\bitcoin\build_msvc\bitcoin-qt\bitcoin-qt.vcxproj]
LINK : fatal error LNK1257: code generation failed [C:\projects\bitcoin\build_msvc\bitcoin-qt\bitcoin-qt.vcxproj]
LINK : fatal error C1047: The object or library file 'c:\tools\vcpkg\installed\x64-windows-static\lib\libzmq-mt-s-4_3_3.lib' was created with an older compiler than other objects; rebuild old objects and libraries [C:\projects\bitcoin\build_msvc\test_bitcoin\test_bitcoin.vcxproj]
LINK : fatal error LNK1257: code generation failed [C:\projects\bitcoin\build_msvc\test_bitcoin\test_bitcoin.vcxproj]
Command exited with code 1
...

```

### Solution

```
curl -H "Authorization: Bearer $APPVEYOR_TOKEN" -H "Content-Type: application/json" -X DELETE https://ci.appveyor.com/api/projects/hebasto/bitcoin/buildcache
```

### Discussion

- https://github.com/bitcoin/bitcoin/pull/17736#issuecomment-565157833

- https://github.com/bitcoin/bitcoin/pull/14086#issuecomment-417842075

- https://github.com/krlmlr/r-appveyor/issues/98

- https://github.com/appveyor/ci/issues/985
