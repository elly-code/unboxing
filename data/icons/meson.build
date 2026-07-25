#
#   ICONS
#

#========================
# Install our icons in all the required sizes
icon_sizes = ['16', '24', '32', '48', '64', '128']

foreach i : icon_sizes
    install_data(
        i + '.svg',
        install_dir: datadir / 'icons' / 'hicolor' / i + 'x' + i / 'apps',
        rename: app_id + '.svg'
    )
    install_data(
        i + '.svg',
        install_dir: datadir / 'icons' / 'hicolor' / i + 'x' + i + '@2' / 'apps',
        rename: app_id + '.svg'
    )
endforeach
