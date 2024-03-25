# shell-module
# Problem: Ansible shell $PATH differs from user's $PATH.
sch: https://www.google.com/search?q=ansible+shell+path+from+user

Bug
- [shell command has unexpected $PATH](https://github.com/ansible/ansible/issues/56044)

# Solution: Set in /etc/environment
from: https://stackoverflow.com/questions/55199479/global-modified-path-in-ansible-not-working-as-expected-from-regular-linux-shel

tasks/main.yml:
```
- name: Add to Global PATH in /etc/environment
  ansible.builtin.replace:
    path: /etc/environment
    regexp: '^PATH="/usr'
    replace: 'PATH="{{ add_paths }}:/usr'
  become: true
  notify: Reset connection

# You have to Reset the connection to pick up PATH changes
- name: Flush handlers
  meta: flush_handlers
```

handlers/main.yml:
```
- name: Reset connection
  meta: reset_connection
```
