# Running service

When running a service via ansible, you may want to make sure that the service is already running
before doing anything. You can use [`wait_for`](http://docs.ansible.com/ansible/lineinfile_module.html) module for this, specify the port and the status.
You can also use log parsing as a detection

If you want to check for exception in runtime after running a service, you can use [`failed_when`](http://docs.ansible.com/ansible/playbooks_error_handling.html#controlling-what-defines-failure),
don't forget to set `changed_when` to false because changed status is useless anyway in this situation

```yml
- hosts: java-server
  tasks:
    - name: Run service
      command: /usr/bin/run-my-service

    - name: Wait for starting
      wait_for:
        port: 8000
        status: started
        delay: 1
        timeout: 120

    - name: Check for execption
      shell: tail -200 /var/log/my-service.log | grep exception
      register: command_result
      changed_when: false
      failed_when: "'exception' in command_result.stdout"
```
