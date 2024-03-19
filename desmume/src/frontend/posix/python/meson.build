dep_x11 = dependency('x11')

py3_inst = import('python').find_installation('python3')

#pybind11_config = find_program('pybind11-config')
#pybind11_config_ret = run_command(pybind11_config, ['--includes'])
#pybind11 = declare_dependency(
#  include_directories: [pybind11_config_ret.stdout().split('-I')[-1].strip()],
#)

python3 = dependency('python3', )

py_dependencies = dependencies + [dep_x11,python3,dep_pybind11]

py_src = [
    'main.cpp',
    '../shared/sndsdl.cpp',
    '../shared/ctrlssdl.cpp',
]

# TODO: why do we have to redeclare it here with one more fs level?
includes = include_directories(
    '../../../../src',
    '../../../../src/libretro-common/include',
    '../../../../src/frontend',
)

py3avlw = py3_inst.extension_module('desmume',
                                    sources: py_src,
                                    dependencies : py_dependencies,
                                    include_directories: includes,
                                    link_language : 'cpp',
                                    link_with : libdesmume,
                                    override_options: [
                                      'cpp_rtti=true',
                                    ]
)





#executable('desmume-cli',
#  cli_src,
#  dependencies: cli_dependencies,
#  include_directories: includes,
#  link_with: libdesmume,
#  install: true,
#)
