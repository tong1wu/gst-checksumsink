project('gst-checksumsink', 'c',
  version : '1.0',
  meson_version : '>= 0.54',
  default_options : [ 'warning_level=1',
                      'buildtype=debugoptimized' ])

gst_req = '>= 1.2'

cc = meson.get_compiler('c')

if cc.has_link_argument('-Wl,-Bsymbolic-functions')
  add_project_link_arguments('-Wl,-Bsymbolic-functions', language : 'c')
endif

gst_dep = dependency('gstreamer-1.0', version : gst_req,
  fallback : ['gstreamer', 'gst_dep'])
gstbase_dep = dependency('gstreamer-base-1.0', version : gst_req,
  fallback : ['gstreamer', 'gst_base_dep'])
gstvideo_dep = dependency('gstreamer-video-1.0', version : gst_req,
  fallback : ['gst-plugins-base', 'video_dep'])

plugins_install_dir = join_paths(get_option('libdir'), 'gstreamer-1.0')

gstchecksumsink = library('gstchecksumsink',
  ['gstchecksumsink.c', 'plugin.c'],
  dependencies : [gst_dep, gstbase_dep, gstvideo_dep],
  install : true,
  install_dir : plugins_install_dir,
)
