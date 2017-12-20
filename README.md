macos munki condition
=====================

[![Build Status](https://travis-ci.org/ANTS-Framework/macos_munki_condition.svg?branch=master)](https://travis-ci.org/ANTS-Framework/macos_munki_condition)

This role is used to manage the admin provided conditions for munki.
For more details about munki conditional items see
[the munki wiki](https://github.com/munki/munki/wiki/Conditional-Items#admin-provided-conditions)

When a condition changes, a file will be created at `/private/tmp/.com.googlecode.munki.updatecheck.launchd`
to activate an update check using `/Library/LaunchDaemons/com.googlecode.munki.managedsoftwareupdate-manualcheck.plist`

Requirements
------------
This role is useless withouth [munki](https://www.munki.org/munki).

Additional preparation is required to take full advantage of the `on_corp` condition.
For more information see the repo by [Graham Gilbert](https://github.com/grahamgilbert/munki_conditions/tree/master/on_corp)

The macOS compatibility scripts have been taken from [Hannes Juutilainen](https://github.com/hjuutilainen).
For more information see [his git repo](https://github.com/hjuutilainen/adminscripts).

Role Variables
--------------
```yml
# Install the templates to this directory
munki_condition__dir: "/usr/local/munki/conditions"
# List of templates to installed
munki_condition__templates:
 - "on_corp"
 - "ants"
# Url for on_corp conditon
# See https://github.com/grahamgilbert/munki_conditions/tree/master/on_corp
munki_condition__on_corp_target: "http:/oncorp.pretencdorp.com//oncorp.plist"
# Path to ants executable
munki_condition__ants_path:
 - "/usr/local/ants/ants.py"
```

Example Playbook
----------------
```yml
- hosts: clients
  vars:
    - munki_condition__on_corp_target: "myurl.io"
  roles:
  - role: macos_munki_conditions
```

License
-------

GPLv3

Author Information
------------------
Part of the [ANTS Framework](https://ants-framework.github.io/)
