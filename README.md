dotfonts
=========

DotFonts or `.fonts` is an ansible role used to install fonts on the system.  
By default it will install these initiall fonts:  

- [Mononoki](https://github.com/madmalik/mononoki/)  
- [Droid Sans Mono Nerd Fonts](https://github.com/ryanoasis/nerd-fonts/tree/master/patched-fonts/DroidSansMono)  
- [Hack Nerd Fonts](https://github.com/ryanoasis/nerd-fonts/tree/master/patched-fonts/Hack)  
- [Font Logos](https://github.com/Lukas-W/font-logos)  


Requirements
------------

* ansible >= 2.11.12

Role Variables
--------------

All the supported variables can be listed from `defaults/main.yml` file, here is more info about it:  


* `dotfonts_install`    - `(dict)`  -  a dictionary that can be used to enable or disable the package installation  
 
* `dotfonts_install_dir`  - `(str)` - a string value for the path where the fonts will be installed. `(defaults "$HOME/.local/share/fonts")`  

* `dotfonts_files`  - `(list)`  - a dict list of fonts to be installed. 



Dependencies
------------

None

Example Playbook
----------------

* Basic default usage
```yaml
---
- hosts: servers
  roles:
  - { role: mrbrandao.dotfonts }
```

* Installing custom fonts  

```yaml
---
- hosts: servers
  vars:
    dotfonts_files:
      - name: MyFont-TTF
        url: "https://myfont.com/myfont.ttf"
        file: "{{ dotfonts_install_dir }}/myfont.ttf"
        extract: false
        clean: false

      - name: MyFont-ZIP
        url: "https://myfont.com/myfont.zip"
        file: "{{ dotfonts_install_dir }}/myfont.zip"
        extract: true # enable the file extraction
        clean: true # remove the zip file after extracted

      - name: GlobalSystemFont
        url: "https://myfont.com/myfont.otf"
        file: "/usr/share/fonts/myfont.otf"
        extract: false 
        clean: false 

  roles:
  - { role: mrbrandao.dotfonts }
```

License
-------

GPL-3.0-only

Author Information
------------------

@mrbrandao - Igor Brandao - https://github.com/mrbrandao
