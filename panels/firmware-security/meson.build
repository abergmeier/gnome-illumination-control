panels_list += cappletname
desktop = 'gnome-@0@-panel.desktop'.format(cappletname)

i18n.merge_file(
  type: 'desktop',
  input: desktop + '.in',
  output: desktop,
  po_dir: po_dir,
  install: true,
  install_dir: control_center_desktopdir
)

sources = files('cc-firmware-security-utils.c',
                'cc-firmware-security-panel.c',
                'cc-firmware-security-dialog.c',
                'cc-firmware-security-help-dialog.c',
                'cc-firmware-security-boot-dialog.c')

resource_data = files('cc-firmware-security-panel.ui',
                      'cc-firmware-security-dialog.ui',
                      'cc-firmware-security-help-dialog.ui',
                      'cc-firmware-security-boot-dialog.ui')

sources += gnome.compile_resources(
  'cc-' + cappletname + '-resources',
  cappletname + '.gresource.xml',
  c_name: 'cc_' + cappletname.underscorify (),
  dependencies: resource_data,
  export: true
)

cflags += '-DGNOMELOCALEDIR="@0@"'.format(control_center_localedir)

deps = common_deps + [
  dependency('libgtop-2.0'),
]

panels_libs += static_library(
  cappletname,
  sources: sources,
  include_directories: [top_inc, common_inc],
  dependencies: deps,
  c_args: cflags
)
