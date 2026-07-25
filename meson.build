project(
    'unboxing',
    ['c', 'vala'],        # The floor is vala
    license: 'GPL-3.0-or-later',
    version: '1.0.3',               # Versioning: first should follow Gtk version, second and third depending how proud you are of the update
    meson_version: '>= 1.1'         # Use meson.option instead of meson_options.txt
    )

app_name = meson.project_name()
app_version = meson.project_version()
nicename = 'Unboxing'
publisher = 'elly-code'

# Ugh i wish i could bin this
app_id = 'io.github.elly_code.' + app_name
app_path = '/io/github/elly_code/' + app_name


#================================
# Preparation

prefix = get_option('prefix')
datadir = get_option('datadir')

development = get_option('development')
if development
  app_id +=  '.devel'
  add_project_arguments('--define=DEVEL', language: 'vala')

endif

gnome = import('gnome')
i18n = import('i18n')
add_project_arguments(
    '-DGETTEXT_PACKAGE="@0@"'.format (app_id),           # 
    '-DG_LOG_DOMAIN="@0@"'.format (app_id),              # Dev builds add the app_id to G_MESSAGES_DEBUG
    '-w',                                                       # Because of Vala we get ten thousand warnings we can do nothing about
    language:'c'
    )


# Play nice with clang
# https://gitlab.gnome.org/GNOME/vala/-/issues/1413#note_1707480
if meson.get_compiler ('c').get_id () == 'clang'
    add_project_arguments('-Wno-incompatible-function-pointer-types', language: 'c')
endif

#================================
# Add subfolders for Meson to look

config_data = configuration_data(
    {
        'APP_NAME': app_name,
        'APP_ID': app_id,
        'APP_PATH': app_path,
        'APP_VERSION': app_version,
        'NICENAME': nicename,
        'PUBLISHER': publisher,
        'LOCALEDIR': prefix / get_option('localedir')
        }
    )

subdir('po')
subdir('data')
subdir('src')
#subdir('tests')


gnome.post_install(
    glib_compile_schemas: true,
    gtk_update_icon_cache: true,
    update_desktop_database: true
)
