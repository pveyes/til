# auto update [atom](https://atom.io)

At this time of writing, Atom in Ubuntu is not auto updated, so I decided to write
an ansible playbook for updating atom. Here is the yml:

```yml
- hosts: localhost
  vars:
    download_path: "/home/{{ ansible_env.USER }}/Downloads/atom.deb"
    download_uri: "https://atom.io/download/deb"
  tasks:
    - name: Download atom latest build
      command: "wget -O {{ download_path }} {{ download_uri }}"
      args:
        creates: "{{ download_path }}"
    - name: Update atom
      sudo: yes
      apt:
        deb: "{{ download_path }}"
    - name: Cleanup (remove downloaded .deb file)
      file:
        path: "{{ download_path }}"
        state: absent
```

Save this as `update-atom.yml` then when you want to update atom, simply run `ansible-playbook update-atom.yml`.

Or you can also put this inside a crontab normally every day (for example every 8 AM)

```
0 8 * * * ansible-playbook update-atom.yml
```
