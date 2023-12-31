project('berkeley-testfloat-3',  'c',
        default_options: ['warning_level=1', 'c_std=gnu99'])

fpcflags = get_option('defines')

platform_data = configuration_data()
platform_data.set('INLINE', 'static inline')
platform_data.set('LITTLEENDIAN', host_machine.endian() == 'little')
configure_file(output: 'platform.h', configuration: platform_data)

tfdir = 'source'
tfinc = include_directories('.', tfdir)

add_project_arguments(
  [
    '-Wno-implicit-fallthrough',
    '-Wno-strict-prototypes',
    '-Wno-unknown-pragmas',
    '-Wno-uninitialized',
    '-Wno-missing-prototypes',
    '-Wno-return-type',
    '-Wno-unused-function',
    '-Wno-missing-format-attribute',
    '-Wno-error',
  ] + meson.get_compiler('c').get_supported_arguments('-Wno-ignored-pragmas'),
  native: false, language: 'c')

tfgencases = [
  tfdir / 'genCases_ui32.c',
  tfdir / 'genCases_ui64.c',
  tfdir / 'genCases_i32.c',
  tfdir / 'genCases_i64.c',
  tfdir / 'genCases_f16.c',
  tfdir / 'genCases_f32.c',
  tfdir / 'genCases_f64.c',
  tfdir / 'genCases_extF80.c',
  tfdir / 'genCases_f128.c',
]

tfwritecase = [
  tfdir / 'writeCase_a_ui32.c',
  tfdir / 'writeCase_a_ui64.c',
  tfdir / 'writeCase_a_f16.c',
  tfdir / 'writeCase_ab_f16.c',
  tfdir / 'writeCase_abc_f16.c',
  tfdir / 'writeCase_a_f32.c',
  tfdir / 'writeCase_ab_f32.c',
  tfdir / 'writeCase_abc_f32.c',
  tfdir / 'writeCase_a_f64.c',
  tfdir / 'writeCase_ab_f64.c',
  tfdir / 'writeCase_abc_f64.c',
  tfdir / 'writeCase_a_extF80M.c',
  tfdir / 'writeCase_ab_extF80M.c',
  tfdir / 'writeCase_a_f128M.c',
  tfdir / 'writeCase_ab_f128M.c',
  tfdir / 'writeCase_abc_f128M.c',
  tfdir / 'writeCase_z_bool.c',
  tfdir / 'writeCase_z_ui32.c',
  tfdir / 'writeCase_z_ui64.c',
  tfdir / 'writeCase_z_f16.c',
  tfdir / 'writeCase_z_f32.c',
  tfdir / 'writeCase_z_f64.c',
  tfdir / 'writeCase_z_extF80M.c',
  tfdir / 'writeCase_z_f128M.c',
]

tftest = [
  tfdir / 'test_a_ui32_z_f16.c',
  tfdir / 'test_a_ui32_z_f32.c',
  tfdir / 'test_a_ui32_z_f64.c',
  tfdir / 'test_a_ui32_z_extF80.c',
  tfdir / 'test_a_ui32_z_f128.c',
  tfdir / 'test_a_ui64_z_f16.c',
  tfdir / 'test_a_ui64_z_f32.c',
  tfdir / 'test_a_ui64_z_f64.c',
  tfdir / 'test_a_ui64_z_extF80.c',
  tfdir / 'test_a_ui64_z_f128.c',
  tfdir / 'test_a_i32_z_f16.c',
  tfdir / 'test_a_i32_z_f32.c',
  tfdir / 'test_a_i32_z_f64.c',
  tfdir / 'test_a_i32_z_extF80.c',
  tfdir / 'test_a_i32_z_f128.c',
  tfdir / 'test_a_i64_z_f16.c',
  tfdir / 'test_a_i64_z_f32.c',
  tfdir / 'test_a_i64_z_f64.c',
  tfdir / 'test_a_i64_z_extF80.c',
  tfdir / 'test_a_i64_z_f128.c',
  tfdir / 'test_a_f16_z_ui32_rx.c',
  tfdir / 'test_a_f16_z_ui64_rx.c',
  tfdir / 'test_a_f16_z_i32_rx.c',
  tfdir / 'test_a_f16_z_i64_rx.c',
  tfdir / 'test_a_f16_z_ui32_x.c',
  tfdir / 'test_a_f16_z_ui64_x.c',
  tfdir / 'test_a_f16_z_i32_x.c',
  tfdir / 'test_a_f16_z_i64_x.c',
  tfdir / 'test_a_f16_z_f32.c',
  tfdir / 'test_a_f16_z_f64.c',
  tfdir / 'test_a_f16_z_extF80.c',
  tfdir / 'test_a_f16_z_f128.c',
  tfdir / 'test_az_f16.c',
  tfdir / 'test_az_f16_rx.c',
  tfdir / 'test_abz_f16.c',
  tfdir / 'test_abcz_f16.c',
  tfdir / 'test_ab_f16_z_bool.c',
  tfdir / 'test_a_f32_z_ui32_rx.c',
  tfdir / 'test_a_f32_z_ui64_rx.c',
  tfdir / 'test_a_f32_z_i32_rx.c',
  tfdir / 'test_a_f32_z_i64_rx.c',
  tfdir / 'test_a_f32_z_ui32_x.c',
  tfdir / 'test_a_f32_z_ui64_x.c',
  tfdir / 'test_a_f32_z_i32_x.c',
  tfdir / 'test_a_f32_z_i64_x.c',
  tfdir / 'test_a_f32_z_f16.c',
  tfdir / 'test_a_f32_z_f64.c',
  tfdir / 'test_a_f32_z_extF80.c',
  tfdir / 'test_a_f32_z_f128.c',
  tfdir / 'test_az_f32.c',
  tfdir / 'test_az_f32_rx.c',
  tfdir / 'test_abz_f32.c',
  tfdir / 'test_abcz_f32.c',
  tfdir / 'test_ab_f32_z_bool.c',
  tfdir / 'test_a_f64_z_ui32_rx.c',
  tfdir / 'test_a_f64_z_ui64_rx.c',
  tfdir / 'test_a_f64_z_i32_rx.c',
  tfdir / 'test_a_f64_z_i64_rx.c',
  tfdir / 'test_a_f64_z_ui32_x.c',
  tfdir / 'test_a_f64_z_ui64_x.c',
  tfdir / 'test_a_f64_z_i32_x.c',
  tfdir / 'test_a_f64_z_i64_x.c',
  tfdir / 'test_a_f64_z_f16.c',
  tfdir / 'test_a_f64_z_f32.c',
  tfdir / 'test_a_f64_z_extF80.c',
  tfdir / 'test_a_f64_z_f128.c',
  tfdir / 'test_az_f64.c',
  tfdir / 'test_az_f64_rx.c',
  tfdir / 'test_abz_f64.c',
  tfdir / 'test_abcz_f64.c',
  tfdir / 'test_ab_f64_z_bool.c',
  tfdir / 'test_a_extF80_z_ui32_rx.c',
  tfdir / 'test_a_extF80_z_ui64_rx.c',
  tfdir / 'test_a_extF80_z_i32_rx.c',
  tfdir / 'test_a_extF80_z_i64_rx.c',
  tfdir / 'test_a_extF80_z_ui32_x.c',
  tfdir / 'test_a_extF80_z_ui64_x.c',
  tfdir / 'test_a_extF80_z_i32_x.c',
  tfdir / 'test_a_extF80_z_i64_x.c',
  tfdir / 'test_a_extF80_z_f16.c',
  tfdir / 'test_a_extF80_z_f32.c',
  tfdir / 'test_a_extF80_z_f64.c',
  tfdir / 'test_a_extF80_z_f128.c',
  tfdir / 'test_az_extF80.c',
  tfdir / 'test_az_extF80_rx.c',
  tfdir / 'test_abz_extF80.c',
  tfdir / 'test_ab_extF80_z_bool.c',
  tfdir / 'test_a_f128_z_ui32_rx.c',
  tfdir / 'test_a_f128_z_ui64_rx.c',
  tfdir / 'test_a_f128_z_i32_rx.c',
  tfdir / 'test_a_f128_z_i64_rx.c',
  tfdir / 'test_a_f128_z_ui32_x.c',
  tfdir / 'test_a_f128_z_ui64_x.c',
  tfdir / 'test_a_f128_z_i32_x.c',
  tfdir / 'test_a_f128_z_i64_x.c',
  tfdir / 'test_a_f128_z_f16.c',
  tfdir / 'test_a_f128_z_f32.c',
  tfdir / 'test_a_f128_z_f64.c',
  tfdir / 'test_a_f128_z_extF80.c',
  tfdir / 'test_az_f128.c',
  tfdir / 'test_az_f128_rx.c',
  tfdir / 'test_abz_f128.c',
  tfdir / 'test_abcz_f128.c',
  tfdir / 'test_ab_f128_z_bool.c',
]

libsoftfloat_proj = subproject('berkeley-softfloat-3', required: true)
libsoftfloat = libsoftfloat_proj.get_variable('libsoftfloat_dep')

libtestfloat = static_library(
  'testfloat',
  files(
    tfdir / 'uint128_inline.c',
    tfdir / 'uint128.c',
    tfdir / 'fail.c',
    tfdir / 'functions_common.c',
    tfdir / 'functionInfos.c',
    tfdir / 'standardFunctionInfos.c',
    tfdir / 'random.c',
    tfdir / 'genCases_common.c',
    tfgencases,
    tfdir / 'genCases_writeTestsTotal.c',
    tfdir / 'verCases_inline.c',
    tfdir / 'verCases_common.c',
    tfdir / 'verCases_writeFunctionName.c',
    tfdir / 'readHex.c',
    tfdir / 'writeHex.c',
    tfwritecase,
    tfdir / 'testLoops_common.c',
    tftest,
  ),
  dependencies: libsoftfloat.partial_dependency(includes: true, compile_args: true),
  c_args: fpcflags,
)

libtestfloat_dep = declare_dependency(
    link_with: libtestfloat,
    dependencies: libsoftfloat,
    include_directories: tfinc,
    compile_args: fpcflags)

libslowfloat = static_library(
  'slowfloat',
  tfdir / 'slowfloat.c',
  dependencies: libsoftfloat.partial_dependency(includes: true, compile_args: true),
  c_args: fpcflags,
)

libslowfloat_dep = declare_dependency(
    link_with: libslowfloat,
    dependencies: libsoftfloat,
    include_directories: tfinc,
    compile_args: fpcflags)
