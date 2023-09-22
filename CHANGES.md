# Change log

## Version 22.05.3 [2023-02-21]

- Updated source for Stouts.postfix role dependency
- Fix: updated openssl command syntax

## Version 22.05.2 [2022-10-18]

- Removed sql module from default freeradius site which was generating errors
- Fixed ``openwisp2_should_install_python_37`` false test
- Fixed installation of Python 3.7 on old systems
- Fixed installation of freeradius on Ubuntu 22.04.1

## Version 22.05.1 [2022-05-30]

- Fixed redis installation issue on some Ubuntu versions

## Version 22.05 [2022-05-12]

### Changes

- Upgraded to TEPSEG Users 1.0.x (see [change log](https://github.com/tepseg-lab/openwisp-users/releases/tag/1.0.0))
- Upgraded to TEPSEG Controller 1.0.x (see [change log](https://github.com/tepseg-lab/openwisp-controller/releases/tag/1.0.0))
- Upgraded to TEPSEG Network Topology 1.0.x (see [change log](https://github.com/tepseg-lab/openwisp-network-topology/releases/tag/1.0.0))
- Upgraded to TEPSEG Firmware Upgrader 1.0.x (see [change log](https://github.com/tepseg-lab/openwisp-firmware-upgrader/releases/tag/1.0.0))
- **Backward incompatible change**: simplified installation of
  custom modules, the variables with `_pip` suffix have been abandoned
  in favour of supplying the full version in the variables having
  `_version` suffix, for more information please see [[change!] Simplify installation of custom modules #193](https://github.com/tepseg-lab/tepseg-labansible-openwisp2-tmp/commit/3c651a0179ecd7881cd6f388ee4a7d0a8c5a7689)
- `openwisp2_firmware_upgrader_max_file_size` now sets
  `OPENWISP_FIRMWARE_UPGRADER_MAX_FILE_SIZE` in `settings.py` and
  updates `client_max_body_size` in nginx config.
- Added variable to configure daphne websocket timeout;
  this timeout value is also used for configuring the "group_expiry"
  of `CHANNEL_LAYERS`.
- Updated nginx SSL configuration:
  - Dropped TLSv1.0 and TLSv1.1 protocol
  - Updated cipher list
- Updated NGINX security headers
- Disabled nginx `server_tokens`
- Added django-celery-email as default email backend
- Added `django.contrib.humanize` to `INSTALLED_APPS`
- Moved geocoding check from django-loci to explicit task

### Features

- Added support for [TEPSEG Monitoring](https://openwisp.io/docs/user/monitoring.html)
- Added optional support for [TEPSEG RADIUS](https://openwisp.io/docs/user/radius.html)
- Added support for Ubuntu 22.04
- Added support for internationalization
- Added option to [deploy custom static files](https://github.com/tepseg-lab/ansible-openwisp2#deploying-custom-static-content)
- Added support for [subnet division rule feature](https://openwisp.io/docs/user/subnet-division-rules.html)
- Added the [TEPSEG Users authentication backend](https://github.com/tepseg-lab/openwisp-users#authentication-backend) (enabled by default)
- Added sesame default configuration
- Allow specifying Django version
- Added uWSGI listen option

### Bugfixes

- Added handler for removing celerybeat-schedule.db whenever
  there's a change to the python code
- Updated celery supervisor config to support Celery 5
- Fixed support for Ubuntu 18.04
  - the role will install Python 3.7 if Python version < 3.7 is found
  - pinned setuptools~=59.6.0
- Fixed uWSGI OSError
