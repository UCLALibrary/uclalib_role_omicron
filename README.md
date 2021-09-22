Omicron [![Build Status](https://app.travis-ci.com/UCLALibrary/uclalib_role_omicron.svg?branch=main)](https://app.travis-ci.com/UCLALibrary/uclalib_role_omicron)
=========

Omicron Initial Installation / Configuration / Maintenance

Requirements
------------

Server requirements:
- SELinux must be disabled
- Firewall must be set to allow 80/443 access

External requirements:
- A postgres database server must be available, either external or on localhost
- Github access token (`git_access_token`)

Since the application repository is private, a Github account with read permissions is required. Credentials are passed as an access token in the `git_access_token` role variable.

Role Variables
--------------

### Defaults

* `omicron_application_name`: (string)
  * (default) omicron
* `omicron_application_dir`: (string/pathname)
  * (default) /opt/omicron
  * based on `omicron_application_name`
* `omicron_groupname`: (string)
  * (default) omicron
  * based on `omicron_username`
* `omicron_username`: (string)
  * (default) omicron
  * based on `omicron_application_name`
* `omicron_version`: (string) Git tag/branch/commit to deploy
  * (default) main
* `omicron_virtualenv_name`: (string/pathname)
  * (default) venv
  * relative to `omicron_application_dir`
* `omicron_ssl_certificate`: (string/pathname)
  * (default) /etc/pki/tls/certs/localhost.crt
* `omicron_ssl_certificate_key`: (string/pathname)
  * (default) /etc/pki/tls/private/localhost.key
* `omicron_db_host`: (string/hostname)
  * (default) localhost
* `omicron_db_name`: (string)
  * (default) omicron
  * based on `omicron_username`
* `omicron_db_user`: (string)
  * (default) omicron
  * based on `omicron_username`
* `omicron_db_pass`: (string)
  * (default) changeme
* `omicron_allowed_hosts`: (array of strings)
  * (default) [ 'localhost' ]
* `omicron_debug`: (boolean)
  * (default) False
* `omicron_secret_key`: (string)
  * (default) changeme
* `omicron_session_cookie_age`: (integer, in seconds)
  * (default) 60 * 60 * 4
* `omicron_superuser_email`: (string/email)
  * (default) user@example.com
* `omicron_superuser_name`: (string)
  * (default) omicron
  * based on `omicron_application_name`
* `omicron_superuser_password`: (string)
  * (default) changeme
* `git_access_token`: (string)
  * Mandatory. No default.

### Vars

* `omicron_packages`: (array of strings)
  * (default) Required packages suitable for EL7


Dependencies
------------

None.

Example Playbook
----------------

    - hosts: omicron-app
      roles:
        - name: uclalib_role_omicron
          omicron_db_host: omicron-db
          omicron_db_pass: 'secret'
          omicron_allowed_hosts:
            - 'localhost'
            - 'omicron'
            - 'omicron-app'
          git_access_token: 'githubtoken'
