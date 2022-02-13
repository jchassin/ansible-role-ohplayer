# [ohplayer](#ohplayer)
=========

This role setup the compilation chain, get the sources, update dependencies and build every thing
This role is defined for Linux Raspbian Raspberry target (testing on bullseye os and on Audiophonics Raspdac Mini LCD HW but should work with whatever other raspberrypi)
This role is written to be used instead of using provided dependency fetch from Linn that does not work anymore since 2021 for non Linn people

Requirements
------------
OS : Raspbian

Role Variables
--------------

Have a look to defaults/main.yaml to get the customizable variables. 

By defaults, it get the openhome repository sources except of ohPlayer itself that it takes from my own repo :
openhome_openssl_repo: https://github.com/openhome/openssl
openhome_ohtools_repo: https://github.com/openhome/ohdevtools
openhome_ohmediaplayer_repo: https://github.com/openhome/ohPipeline
openhome_ohnet_repo: https://github.com/openhome/ohNet
openhome_ohnetgenerated_repo: https://github.com/openhome/ohNetGenerated
openhome_ohplayer_repo: https://github.com/jchassin/ohPlayer
openhome_ohwafhelpers_repo: https://github.com/openhome/ohWafHelpers

Default destination folder : 
openhome_folder: /home/pi/openhome_player

See example to see how to override variables

Dependencies
------------
N/A

Example Playbook
----------------

Install the role : 
ansible-galaxy install  jchassin.ohplayer


You can put this in a playbook myPb.yaml : 

---
- name: installing audio streamers task
  hosts: my_host
  vars:
    - openhome_folder: /home/USERNAME/openhome
  roles:
    - role: jchassin.ohplayer

and then execute : 
ansible -i YourInventoryFolder myPb.yaml

License
-------

BSD

Author Information
------------------

Limitation:

- issue to install automatically on lib, you need to install manually gtk+-3-dev
	sudo apt-get install gtk+-3-dev

