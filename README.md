libLTC for Windows
------------------

This repository provides a Visual C++ solution to build [libltc](http://x42.github.io/libltc/) as `libltc.dll` for Windows.
To build your own DLL, open [`./msvc/libltc.sln`](./msvc/libltc.sln) by Visual Studio and build the solution.
Your DLL will be generated as `./msvc/x64/{Release,Debug}/libltc.dll`.
You can also find `example_encode.exe`, `ltcdecode.exe`, and `ltcencode.exe` in the same directory.
Once the DLL is compiled, you can import [`./src/ltc.h`](./src/ltc.h) and `libltc.{dll,lib}` into your own project.

Notice that the exported functions are not declared with `__declspec(dllimport)` nor `__stdcall` though these are popular in other DLLs.  This design is based on the following pros and cons.
* Pros:
  * We do not need to modify the original source files in `./src/`.
* Cons (not really):
  * We need to edit [`./msvc/libltc.def`](./msvc/libltc.def) to [specify the functions to be exported](https://docs.microsoft.com/en-us/cpp/build/exporting-from-a-dll-using-def-files).
  * We may want to use ["whole program optimization"](https://docs.microsoft.com/en-us/cpp/build/importing-function-calls-using-declspec-dllimport).  This option is enabled by default for `Release` builds.
  * [`__cdecl`](https://docs.microsoft.com/en-us/cpp/cpp/cdecl) is used instead of [`__stdcall`](https://docs.microsoft.com/en-us/cpp/cpp/stdcall).




libLTC
------

Linear (or Longitudinal) Timecode (LTC) is an encoding of SMPTE timecode data
as a Manchester-Biphase encoded audio signal.
The audio signal is commonly recorded on a VTR track or other storage media.

libltc provides functionality to encode and decode LTC audio from/to
SMPTE or EBU timecode, including SMPTE date support.

libltc is the successor of [libltcsmpte](https://sourceforge.net/projects/ltcsmpte/).
For more information, please see the FAQ in the documentation.

Documentation
-------------

The API reference, examples, as well as introduction can be found at

https://x42.github.io/libltc/

This site is part or the source-code in the doc/ folder.
