Role Name [![Build Status](https://travis-ci.org/UCLALibrary/uclalib_role_template.svg?branch=master)](https://travis-ci.org/UCLALibrary/uclalib_role_template)
=========

Omicron Initial Installation / Configuration / Maintenance

Requirements
------------

SELinux must be disabled. Firewall must be set to allow 80/443 access. A postgres database server must be available.

Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

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
* `omicron_version`: (string)
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

### Vars

* `omicron_packages`: (array of strings)
	* (default) Required packages suitable for EL7


Dependencies
------------

None.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }
