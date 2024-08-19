# dll2proj

`dll2proj` is a script to convert a DLL file into a Visual Studio project by taking all the exports and creating their respective function stubs (with a dummy signature and implementation).

## Usage

`dll2proj` takes two arguments: the path to the DLL file and the output directory for the mock project. It parses all the exported symbols, then create a complete Visual Studio project with a header file containing the function stubs and a source file with the dummy implementation.

```
usage: dll2proj.py [-h] -d DLL_FILE -p PROJECT

Generates a mock C++ DLL project based on DLL exports.

options:
  -h, --help            show this help message and exit
  -d DLL, --dll DLL     Path to the DLL file.
  -p PROJECT, --project PROJECT
                        Output directory for the mock project.
```

After successfully running the script, you will find a Visual Studio project in the specified output directory to be used as a starting point for writing another DLL that will be compatible with the original one.

In the output directory, run the `prep-cmake.bat` script to generate the Visual Studio project files.

After building the project, you will have a header file and a library file that can be used to link against the original DLL from your other projects. Feel free to clean up the header file and keep at least one symbol that will be used to link/refer to the original DLL. Please refer to 'main.cpp' for an example of how to use the generated library.