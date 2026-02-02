Download cmake 3.29.9
Download msys2 and install to C:\msys2
Git clone vcpkg and bootstrap.sh
Update CMakePresets.json to use new debug and release presets:
        {
            "name": "debug",
            "inherits": ["base"],
            "displayName": "Debug",
            "architecture": { "value": "x64", "strategy": "external" },
            "cacheVariables": {
                "CMAKE_BUILD_TYPE": "Debug",
                "CMAKE_CXX_COMPILER": "cl.exe",
                "CMAKE_TOOLCHAIN_FILE": "E:/Projects/Github/Microsoft/vcpkg/scripts/buildsystems/vcpkg.cmake",
                "VCPKG_EXECUTABLE": "E:/Projects/Github/Microsoft/vcpkg/vcpkg.exe",
                "VCPKG_ROOT": "E:/Projects/Github/Microsoft/vcpkg"
            },
            "environment": {
            }
        },
        {
            "name": "release",
            "inherits": ["base"],
            "displayName": "Release",
            "architecture": { "value": "x64", "strategy": "external" },
            "cacheVariables": {
                "CMAKE_BUILD_TYPE": "Release",
                "CMAKE_CXX_COMPILER": "cl.exe",
                "CMAKE_TOOLCHAIN_FILE": "E:/Projects/Github/Microsoft/vcpkg/scripts/buildsystems/vcpkg.cmake",
                "VCPKG_EXECUTABLE": "E:/Projects/Github/Microsoft/vcpkg/vcpkg.exe",
                "VCPKG_ROOT": "E:/Projects/Github/Microsoft/vcpkg"
            },
            "environment": {
            }
        }
Set VCPKG_MSYS2_PATH to C:\msys2
Set VCPKG_ROOT to [path to repo directory that should have vcpkg.exe in it]
Allow for VSCode to configure the build directory via cmake
Open via Win+Search "x64 Native Tools Command Prompt for VS 2022"
	cd E:\Path\to\mod\project\repo
	cmake --preset release
	cmake --build build/release
The dll should now exist in the release folder