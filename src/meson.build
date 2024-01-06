pkgdatadir = get_option('prefix') / get_option('datadir') / meson.project_name()
moduledir = pkgdatadir / 'simple_gtk4_calculator'
gnome = import('gnome')

gnome.compile_resources('simple-gtk4-calculator',
  'simple-gtk4-calculator.gresource.xml',
  gresource_bundle: true,
  install: true,
  install_dir: pkgdatadir,
)

python = import('python')

conf = configuration_data()
conf.set('PYTHON', python.find_installation('python3').path())
conf.set('VERSION', meson.project_version())
conf.set('localedir', get_option('prefix') / get_option('localedir'))
conf.set('pkgdatadir', pkgdatadir)

configure_file(
  input: 'simple-gtk4-calculator.in',
  output: 'simple-gtk4-calculator',
  configuration: conf,
  install: true,
  install_dir: get_option('bindir'),
  install_mode: 'r-xr--r--'
)

simple_gtk4_calculator_sources = [
  '__init__.py',
  'main.py',
  'window.py',
]

install_data(simple_gtk4_calculator_sources, install_dir: moduledir)
