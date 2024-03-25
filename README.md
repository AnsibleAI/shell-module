# shell-module
# Problem: Ansible shell $PATH differs from user's $PATH.
sch: https://www.google.com/search?q=ansible+shell+path+from+user

Bug
- [shell command has unexpected $PATH](https://github.com/ansible/ansible/issues/56044)

## Solution: Set in /etc/environment
https://stackoverflow.com/questions/55199479/global-modified-path-in-ansible-not-working-as-expected-from-regular-linux-shel
