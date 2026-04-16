project('resize2', 'cpp',
  default_options : ['buildtype=release', 'b_ndebug=if-release', 'c_std=c89', 'cpp_std=c++17'],
  meson_version : '>=1.0.0',
  version : '0.4.1'
)

sources = [
    'resize.cpp'
]

py = import('python').find_installation()
vapoursynth_include_command = run_command(
    py,
    '-c',
    'import vapoursynth as vs; print(vs.get_include())',
    check: true,
)
vapoursynth_include = include_directories(vapoursynth_include_command.stdout().strip())

deps = [dependency('zimg_patched')]

cxx = meson.get_compiler('cpp')

# GH-18: Prefer internal, patched zimg symbols over any external ones.
add_project_link_arguments(cxx.get_supported_link_arguments('-Wl,-Bsymbolic-functions'), language : 'cpp')

shared_module('resize2', sources,
    dependencies: deps,
    include_directories: [vapoursynth_include],
    link_args: get_option('link-static') ? ['-static'] : [],
    install: true,
    install_dir: py.get_install_dir(pure: false) / 'vapoursynth' / 'plugins',
    gnu_symbol_visibility: 'hidden',
)
