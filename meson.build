project('bgfx', 'cpp', 'objcpp')
bx = subproject('bx')
include = include_directories('3rdparty', '3rdparty/dxsdk/include', '3rdparty/khronos', 'include')

if host_machine.system() == 'darwin'
  source = 'src/amalgamated.mm'
  deps = dependency('appleframeworks', modules : ['OpenGL'])
else
  source = 'src/amalgamated.cpp'
  deps = []
endif

lib = static_library('bgfx', source, include_directories : [include, bx.get_variable('include')], dependencies : deps)
