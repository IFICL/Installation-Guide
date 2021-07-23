# Installation Guide for librealsense in MacOS

## Step 1 - Install librealsense
Currently, librealsense installation only support Mac with Intel chips, we can follow the [official guide](https://github.com/IntelRealSense/librealsense) to build from source, or we can install it via `homebrew`
```bash
brew install librealsense
```

Then we can link the intalled librealsense2 to the location it has to be
```
ln -s /usr/local/include/librealsense2 /usr/local/include/librealsense
```

## Step 2 - Install pyrealsense python warpper
After we succeed to install librealsense, we need to install python warpper indivdually. Sadly, the official package doesn't support `pip` in MacOS, so we have to build it from source. Maybe the issue will be solved in future.

First, we need to claim some system path to avoid the error: add following line to your `.bashrc` or `.zshrc`
```bash
export OPENSSL_ROOT_DIR="/usr/local/opt/openssl@1.1/"
export PATH="/usr/local/opt/openssl@1.1/bin:$PATH"
export LDFLAGS="-L/usr/local/opt/openssl@1.1/lib"
export CPPFLAGS="-I/usr/local/opt/openssl@1.1/include"
export PKG_CONFIG_PATH="/usr/local/opt/openssl@1.1/lib/pkgconfig"
```

Then we can build it from source
```bash
git clone https://github.com/IntelRealSense/librealsense
mkdir build && cd build
cmake ../ -DBUILD_PYTHON_BINDINGS=bool:true
make -j4
sudo make install
```

In the end, export `PYTHONPATH=$PYTHONPATH:/usr/local/lib` either on console or in your `.bashrc` or `.zshrc`, then you can `import pyrealsense2` from everywhere
