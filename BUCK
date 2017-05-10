include_defs('//BUCKAROO_DEPS')

posix_sources = glob([
  'src/posix/**/*.cpp',
])

windows_sources = glob([
  'src/win32/**/*.cpp',
])

cxx_library(
  name = 'locale', 
  header_namespace = 'boost',
  exported_headers = subdir_glob([
    ('include/boost', '**/*.hpp'),
  ]),
  srcs = glob([
    'src/**/*.cpp'
  ], 
  excludes = posix_sources + windows_sources),
  platform_srcs = [
    ('default', posix_sources),
    ('^macos.*', posix_sources),
    ('^linux.*', posix_sources),
    ('^windows.*', windows_sources),
  ],
  compiler_flags = [
    '-std=c++11', 
  ],
  platform_compiler_flags = [
    ('default', ['-DBOOST_LOCALE_WITH_ICONV']), # TODO: Remove once macOS platform name is known 
    ('^macos.*', ['-DBOOST_LOCALE_WITH_ICONV']),
    ('^linux.*', []),
    ('^windows.*', []),
  ],
  visibility = [
    'PUBLIC',
  ],
  deps = BUCKAROO_DEPS,
)
