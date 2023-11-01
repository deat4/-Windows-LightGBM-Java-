# -Windows-LightGBM-Java-
本文旨在指导读者如何在 Windows 系统上为 LightGBM 构建 Java 包装器。其中会涉及到工具和依赖的安装、构建过程。
首先通过MinGW-w64来构建
 MinGW-w64 安装步骤:

为 Windows 安装 Git、CMake 和 MinGW-w64。
安装 SWIG 和 Java（确保 JAVA_HOME 被正确设置）。
执行以下命令:
bash
Copy code
git clone --recursive https://github.com/microsoft/LightGBM
cd LightGBM
mkdir build
cd build
cmake -G "MinGW Makefiles" -DUSE_SWIG=ON ..
mingw32-make.exe -j4
结果中 .jar 文件会在 LightGBM/build 文件夹中，而 .dll 文件会在 LightGBM/ 文件夹中。
注意：如果遇到 sh.exe was found in your PATH 的错误，你可能需要再次运行 cmake -G "MinGW Makefiles" -DUSE_SWIG=ON .. 命令。
然后
打开 IntelliJ IDEA 并创建一个新的 Java 项目。
在项目结构中，选择模块部分。
点击“依赖”选项卡，然后点击“+”按钮添加外部JARs或模块。
浏览到你之前生成的 .jar 文件位置并选择它，以将其添加到项目中。
对于 .dll 文件，你需要确保它们在 Java 系统路径或 IDEA 的运行配置路径中。你可以将这些 .dll 文件放在项目目录下或其他位置，并确保在运行时系统能够找到它们。
在运行 Java 程序时，如果涉及到这些 .dll 文件，确保 -Djava.library.path 指向这些 .dll 文件的位置。
这样环境就搭建好了，但操作步骤依然十分繁琐，为了简化操作我们使用maven添加lightgbm4j，GitHub链接如下：https://github.com/metarank/lightgbm4j/tree/main 来简化操作

