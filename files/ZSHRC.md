# Zshrc files

Several sample `.zshrc` files are provided. Set the `zshrc_level` variable to select the file to use. If you don't want to install any `.zshrc` file, use:
```yaml
zshrc_level: none
```
When the play runs, it checks the value of `zshrc_level`. If it is not one of the defined values, it is reset to `zshrc_level: none`.

## 1 Zsh Only
File `.zshrc.1.zsh-only`.

This file contains configuration from `zsh-newuser-install` and `compinstall` only. To install this file use:
```yaml
zshrc_level: zsh-only
```

## 2 Plus Oh-My-Zsh
File `.zshrc.2.plus-oh-my-zsh`.

This file contains everything from file 1, plus the default configuration from `oh-my-zsh`. This sets the theme to Robby Russell:
```shell
ZSH_THEME="robbyrussell"
```
To install this file use:
```yaml
zshrc_level: plus-oh-my-zsh
```

## 3 Plus PowerLevel10K no configuration
File `.zshrc.3.plus-p10k-no-config`.

This file contains everything from file 2, and only changes the theme to PowerLevel10K:
```shell
ZSH_THEME="powerlevel10k/powerlevel10k"
```
To install this file use:
```yaml
zshrc_level: plus-p10k-no-config
```

## 4 Plus PowerLevel10K configuration
File `.zshrc.4.plus-powerlevel-10k`.

This file contains everything from file 3, plus the instant prompt, and the command to source the PowerLevel10K configuration, which is actually contained in the file `.p10k.zsh`.
To install this file use:
```yaml
zshrc_level: plus-powerlevel-10k
```
This setting will also install an opinionated PowerLevel10K configuration in `.p10K.zsh`.

## 5 Custom Zshrc and P10K
These files are not included in the repo - they must be provided on a mounted volume named `Shurroo`.
To install custom files use:
```yaml
zshrc_level: custom
```
This setting will install the following files: 
```shell
/Volumes/Shurroo/oh-my-zsh-p10k/.zshrc
/Volumes/Shurroo/oh-my-zsh-p10k/.p10K.zsh
```
