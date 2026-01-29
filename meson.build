project('resize2', 'cpp',
  default_options : ['buildtype=release', 'b_ndebug=if-release', 'c_std=c89', 'cpp_std=c++17'],
  meson_version : '>=1.0.0',
  version : '0.3.4'
)

sources = [
    'resize.cpp'
]

vapoursynth_dep = dependency('vapoursynth').partial_dependency(compile_args : true, includes : true)

deps = [
    vapoursynth_dep,
    dependency('zimg_patched'),
]

cxx = meson.get_compiler('cpp')

# GH-18: Prefer internal, patched zimg symbols over any external ones.
add_project_link_arguments(cxx.get_supported_link_arguments('-Wl,-Bsymbolic-functions'), language : 'cpp')

shared_module('resize2', sources,
    dependencies: deps,
    link_args: get_option('link-static') ? ['-static'] : [],
    install : true,
    install_dir : join_paths(vapoursynth_dep.get_variable(pkgconfig: 'libdir'), 'vapoursynth'),
    gnu_symbol_visibility : 'hidden',
)