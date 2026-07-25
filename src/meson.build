#
# Sources
#

#================================
# Config.vala allows us to set variables in Meson, for the Vala app to use later

config_file = configure_file(
    input: 'Config.vala.in',
    output: '@BASENAME@',
    configuration: config_data
    )

#================================
dependencies = [
        dependency('gtk4', version: '>=4.14'),          # Because of working on oldbuntu.  Should be 4.16: var(--prop) css notation for theming
        dependency('granite-7', version: '>=7.6.0'),    # Version both in appcenter and flathub
        dependency('gobject-2.0'),
        dependency('packagekit-glib2'),                 # APT handling
    ]

#================================
sources = files (
    'Utils' / 'EnumToLocText.vala',
    'Utils' / 'FileOperations.vala',
    'Views' / 'AbstractView.vala',
    'Views' / 'ErrorView.vala',
    'Views' / 'MainView.vala',
    'Views' / 'ProgressView.vala',
    'Views' / 'SuccessView.vala',
    'Application.vala',
    'MainWindow.vala',
    'Welcome.vala',
    'Backend.vala',
)

#================================
# There it is. The exe. The cause of all this mess.

executable(
    app_id,
    gresource,
    config_file,
    sources,
    dependencies: dependencies,
    install : true
)
