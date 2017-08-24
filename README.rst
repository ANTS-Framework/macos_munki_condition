macos munki condition
=====================

Description
------------
This role is used to manage the admin provided conditions for munki.
For more details about munki conditional items see
`the munki wiki <https://github.com/munki/munki/wiki/Conditional-Items#admin-provided-conditions>`_

Usage
------
Add your condition scripts to the templates folder and use the
munki\_condition\_\_templates variables in group\_vars or host\_vars
to decide which conditions should be installed on the client.

Depending on the condition scripts, there might be variables you want to
overwrite for your environment. Use group\_vars or host\_vars to do that.

Notes
-------
For more information on the on\_corp fact see the repo by
`Graham Gilbert <https://github.com/grahamgilbert/munki_conditions/tree/master/on_corp>`_
