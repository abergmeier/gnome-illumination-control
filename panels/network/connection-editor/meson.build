name = 'connection-editor'

sources = files(
  'ce-ip-address-entry.c',
  'ce-netmask-entry.c',
  'ce-page-8021x-security.c',
  'ce-page-details.c',
  'ce-page-ethernet.c',
  'ce-page-ip4.c',
  'ce-page-ip6.c',
  'ce-page-security.c',
  'ce-page-vpn.c',
  'ce-page-wireguard.c',
  'ce-page-wifi.c',
  'ce-page.c',
  'net-connection-editor.c',
  'vpn-helpers.c'
)

resource_data = files(
  '8021x-security-page.ui',
  'connection-editor.ui',
  'details-page.ui',
  'ethernet-page.ui',
  'ip4-page.ui',
  'ip6-page.ui',
  'security-page.ui',
  'vpn-page.ui',
  'wireguard-page.ui',
  'wireguard-peer.ui',
  'wifi-page.ui'
)

c_name = 'net-' + name

sources += gnome.compile_resources(
  c_name + '-resources',
  name + '.gresource.xml',
  c_name: c_name.underscorify(),
  dependencies: resource_data,
  export: true
)

libconnection_editor = static_library(
  name,
  sources: sources,
  include_directories: [top_inc, common_inc, network_inc],
  dependencies: deps,
  c_args: cflags,
)
