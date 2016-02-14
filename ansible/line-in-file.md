# [lineinfile](http://docs.ansible.com/ansible/lineinfile_module.html) module

This ansible module will search for a line in a file and ensure that it is present or absent

I use it to enable sudo without password for my user in ubuntu server

```yml
- name: Allow user to run sudo without password
  sudo: yes
  lineinfile:
    dest: /etc/sudoers
    line: "{{ user }} ALL=(ALL) NOPASSWD: ALL"
    state: present
```
