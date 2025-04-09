# OpenFST for Windows

OpenFst is a library for constructing, combining, optimizing, and searching weighted finite-state transducers (FSTs), maintained by Google and released under the [Apache 2.0 license](./LICENSE). 
The home page for the library is located at http://openfst.org/. 
Check the [original README file](./README) for the current version, as we are not updating this file with the current release version. 
Make sure also to check the [NEWS](./NEWS) file for the latest changes. This file is part of the original distribution.

## Build

You will need CMake and a recent enough Visual Studio. 
Microsoft provides an option to download the free Visual Studio [Community Edition](https://visualstudio.microsoft.com/downloads/), which is adequate.

```
cmake -G Ninja -DCMAKE_INSTALL_PREFIX:PATH=../Release -DCMAKE_BUILD_TYPE=Release -DBUILD_SHARED_LIBS=OFF -B build .
cmake --build build --target install --config Release -j 10
```

## Maintainers

The repository is maintained by [@SystemPanic](https://github.com/SystemPanic) and based on the previous work of [@kkm000](https://github.com/kkm000/openfst).

Open an issue to let us know if you discover a problem with the port. 
Be sure to include a problem description, error text id any, and the Visual Studio version and CMake version.

Since we do not (by the definition of port) extend the OpenFST library itself, please contact its authors with questions and suggestions related to the original library.

---

_Copyright (c) 2008-current Google Inc._
_Copyright (c) 2016-current SmartAction LLC (kkm)_  
_Copyright (c) 2016-current Johns Hopkins University (J. Trmal)_