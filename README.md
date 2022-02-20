Ansible Role: Shurroo Oh-My-Zsh and PowerLevel10K
=================================================

Installs `Oh-My-Zsh` and `PowerLevel10K` on macOS using Homebrew and optionally installs configuration files. There are no role dependencies but please read the Requirements.

Requirements
------------

* Intel Mac (x86_64) (Apple Silicon, arm64, is not yet supported)
* macOS >= 12.1 (Monterey)
* XCode Command Line Tools (CLT)
* Homebrew
* Ansible >= 2.11

Note that the role is supported for local execution **only**.

Role Variables
--------------

If you want to install configuration files, set the value of `zshrc_level` appropriately:
```yaml
zshrc_level:
  none                 # Don't install .zshrc or .p10k.zsh
  zsh-only             # Basic zsh configuration only
  plus-oh-my-zsh       #   + Oh-My-Zsh configuration with "robbyrussell" theme
  plus-p10k-no-config  #   + PowerLevel10K theme
  plus-powerlevel-10k  #   + PowerLevel10K configuration in .p10k.zsh
  custom               # Custom configuration from /Volumes/Shurroo/oh-my-zsh-p10k 
```
Please read `files/ZSHRC.md` for more details. The default setting is `none`. If an unknown value is encountered, it is reset to `none` for safety. If you wish to use custom files, these must exist on a mounted volume named `Shurroo`, and in an `oh-my-zsh-p10k` folder, like this:
```shell
/Volumes/Shurroo/oh-my-zsh-p10k/.zshrc
/Volumes/Shurroo/oh-my-zsh-p10k/.p10K.zsh
```
If `custom` is specified, but the file does not exist, no alternative is copied.

If you want to set the default shell, please ensure you provide a user name, for example:
```yaml
user_name: Groot
```

You can enable a log summary to `~/.shurroo/log/` by setting:
```yaml
write_log_file: true
```
The log file is timestamped, so you can differentiate multiple plays, for example `oh-my-zsh-p10k-2022-0219-1817.log`. Even though a new file is created on each play, the log write does not add to the `changed` task count.

Dependencies
------------

There are no dependencies on other Ansible Galaxy roles, but you must have Homebrew installed. This role deliberately **does not** install Homebrew, and fails if Homebrew is not installed.

You can install Homebrew using the Shurroo [installer](https://github.com/Shurroo/install), or by following the Homebrew [instructions](https://brew.sh/). Note that either of these methods will install the Command Line Tools if they are needed.

Example Playbook
----------------

```yaml
- hosts: localhost
  connection: local
  roles:
    - role: Shurroo.oh-my-zsh-p10k
  vars:
    write_log_file: true
    zshrc_level: plus-powerlevel-10k
    user_name: Groot
```

Custom Plugins
--------------

This role does not install any custom plugins for Oh-My-Zsh.

Source Files
------------

Playing the role using `shurroo play oh-my-zsh-p10k` will automatically discover and use a custom playbook file if it exists. The playbook file must be on a mounted volume named `Shurroo`, and in an `oh-my-zsh-p10k` folder, like this:
```shell
/Volumes/Shurroo/oh-my-zsh-p10k/oh-my-zsh-p10k.yml
```

Source files will be copied from a mounted volume named `Shurroo` if they exist. This method allows convenient use of a flashdrive or mounted network disk containing dotfiles, configuration files and secrets. This role will copy the following files if they are found and `zshrc_level` is set to `custom`:
```zsh
/Volumes/Shurroo/oh-my-zsh-p10k/.zshrc
/Volumes/Shurroo/oh-my-zsh-p10k/.p10K.zsh
```

Project Name
------------

The project was originally inspired from the [Superlumic](https://github.com/superlumic/superlumic) project by [Roderik van der Veer](https://github.com/roderik). When I started on a replacement, I searched for a name with some meaning like "launch", "fire up", "bootstrap" or similar. I eventually settled on Hindi "shurroo" (शुरू). [Google Translate](https://translate.google.com/?sl=en&tl=hi&text=begin&op=translate) tells me "shurroo" means "begin", so this works nicely. Note that the official latin spelling has only one "r", but that name was already taken on GitHub, so I added a second "r". See the parent [Shurroo](https://github.com/Shurroo/shurroo) project for more details.


License
-------

[BSD-3-Clause](https://spdx.org/licenses/BSD-3-Clause.html)

Author Information
------------------

Ian Taylor ([IanTaylorFB](https://github.com/IanTaylorFB)), Co-Founder and CTO at [FlyingBinary Ltd](https://flyingbinary.com).
