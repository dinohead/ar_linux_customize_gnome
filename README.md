# Linux Customize GNOME Desktop

This Ansible role customizes GNOME Desktop on a Linux system by performing the following actions:
* Install GNOME-Tweak tool
* Set default session for user to GNOME 3
* Set global dark theme
* Install and configure GNOME 3 Dash-to-dock extension
* Disable screen lock and turn off screen timeout
* Allow icons on the desktop
* Hide trash, connected volumes, and home icon on the desktop
* Show date in top bar
* Disable desktop animations
* Set 'Do not report technical problems' to true
* Add minimize and maximize buttons to windows
* Use list and tree views for files
* Show hidden files in file browser
* Show directories in file browser
* Add root bookmark to file browser
* Add owner, group, and permissions columns to the file browser
* Use small icons in the file browser
* Show 'create link' and 'delete permanently' options in the file browser
* Add line numbers to Text Editor

## Requirements

* The role uses magic variables to determine the Linux distribution type. Ansible facts must be available.
* This role uses root to install system packages and repositories.
* This role uses system package manager install packages. The host must have package sources setup.

## Role Variables

All over-writable variables used in this role are defined in defaults/main.yml.

You can override the variables in any standard Ansible-way (e.g. group_vars, host_vars, playbook variables, command-line, etc.).

The variables in this role include:

|parameter                 |required|default           |choices|comments|
|:-------------------------|:-------|:-----------------|:------|:-------|
|linux_customize_gnome_user|false   |`{{ansible_user}}`|       |The linux user to apply GNOME Customizations to.|
|linux_customize_gnome_src |false   |                  |       |A list of dictionaries. Each dictionary contains two keys: `version` and `url`. `version` corresponds to a GNOME Shell version (ex: 3.2, 3-16, 3-28) and `url` is the url to find the associated GNOME Dash-to-dock plugin. The intention is to provide the ability to use the role offline by staging the dash-to-dock plugins on an HTTP server. The role will determine the current GNOME shell version and then look through this list of dictionaries to find and download the correct GNOME dash-to-dock plugin. If you are on an internet-connected system, this variable should not need to be modified. |

## Example Playbook

Customize GNOME
```yaml
    - hosts: servers
      roles:
        - ar_linux_customize_gnome
```

## Author Information

|Author              |E-mail                   |
|:-------------------|:------------------------|
|Derek 'dRock' Halsey|derek.halsey@dinohead.com|

## License

MIT License

Copyright (c) 2019 Dinohead LLC

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

## Role Development Information

### Testing

### Contributing

1. Fork it
1. Create your feature branch (`git checkout -b my-new-feature`)
1. Commit your changes (`git commit -am 'Add some feature'`)
1. Push to the branch (`git push origin my-new-feature`)
1. Create new Pull Request

### Git SCM
Please refer to the .gitignore file and update accordingly depending on your
development environment, etc.  The particular file was generated at 
[gitignore.io](https://www.gitignore.io/) and contains settings for the following:
  - Ansible
  - Python
  - Vim
  - Eclipse
  - IntelliJ IDEA
  - Linux
  - Windows
  
### Versioning
Please update [VERSION.md](./VERSION.md) as you release new versions of your role and try to
abide by [Semantic Versioning](http://semver.org/spec/v2.0.0.html).

### Self-contained
Please try to keep this role as self-contained as possible such that it may be
simply installed (e.g. `ansible-galaxy install`) and applied as part of a 
playbook.
