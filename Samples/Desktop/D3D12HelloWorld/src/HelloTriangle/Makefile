CC=clang-cl
TARGET=x86_64-pc-windows-msvc
LIBS=kernel32.lib user32.lib d3d12.lib Shell32.lib D3DCompiler.lib DXGI.lib

SRCS=$(wildcard ./*.cpp)
XWIN=$(HOME)/Personal/graphics-playground/directx/xwin/
INCLUDE_FLAGS=-I$(shell dirname `which clang`)/../resource-root/include/ -I./packages/Microsoft.Direct3D.D3D12.1.614.1/build/native/
LINK_FLAGS=/libpath:$(XWIN)/Windows\ Kits/10/lib/10.0.26100/um/x86_64/ /libpath:$(XWIN)/Windows\ Kits/10/lib/10.0.26100/ucrt/x86_64/ /libpath:$(XWIN)/VC/Tools/MSVC/14.44.17.14/lib/x86_64/

build:
	$(CC) \
	/EHsc /DUNICODE /D_UNICODE \
	/winsysroot $(XWIN) \
	$(INCLUDE_FLAGS) \
	-Wno-address-of-temporary \
	-target $(TARGET) \
	-x "c++" $(SRCS) \
	-fuse-ld=lld-link /link \
    $(LINK_FLAGS)
	$(LIBS)
