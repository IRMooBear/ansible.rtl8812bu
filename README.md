[![Build Status](https://travis-ci.com/IRMooBear/ansible.rtl8812bu.svg?branch=master)](https://travis-ci.com/IRMooBear/ansible.rtl8812bu)

Install 8812BU
=========

Ansible role to automatically download and compile drivers for RealTek RTL8812BU WIFI adapters.

Dependencies
--------------
This role build the driver from https://github.com/cilynx/rtl88x2BU_WiFi_linux_v5.3.1_27678.20180430_COEX20180427-5959.

Role Variables
--------------
    compile_threads: "{{ ansible_processor_cores }}"
The number of threads to use during compile time
    
    rtl8812bu_version: ac11dcb1c199d1f0435f583334e327c497f2dd4f
    
Git version from https://github.com/cilynx/rtl88x2BU_WiFi_linux_v5.3.1_27678.20180430_COEX20180427-5959.git to pull.    
    
    rtl8812bu_mac: 000000000000

If you know your chip mac address, this will configure it.
    
    rtl8812bu_wpa_supplicant: yes
    
Create separate WPA supplicant file from template.
    
    rtl8812bu_load_module_on_startup: no
    
Autoload module on startup.    
    
    rtl8812bu_config_i386: no
    rtl8812bu_config_rpi: yes
    
Set to compile for RPI by default, turn this off if used on i386...    
    
    rtl8812bu_authentications:
      -
        ssid: ssid_name
        password: password
        key_management: WPA-PSK
        priority: 1
        id_str: ssid_name
        
A list of authentication used for the WPA template.        
        
Example Playbook
----------------

1. Set rtl8812bu_authentications variable somewhere to auto build the wpa_supplicant file.
2. Set rtl8812bu_mac address!

Example usage:

    - hosts: servers
      roles:
         - { role: irmoobear.rtl8812bu, rtl8812bu_mac: 1234..., rtl8812bu_authentications: my_auth }

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
