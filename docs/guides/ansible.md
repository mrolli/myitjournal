# Ansible

## Articles

* [Using DNS as an Ansible dynamic Inventory](https://medium.com/@remie/using-dns-as-an-ansible-dynamic-inventory-e65a2ed6bc9)
* [Checking Controlling Task Execution, Orchestration and Scope](https://dev.to/admantium/ansible-checking-and-controlling-task-execution-orchestration-and-scope-32ei)

## Recipes

### Check if a line is present in a file

Use this recipe in a molecule verify playbook to check if a certain line is
present or absent in a file. Keep `state:absent` and work with the
`failed_when` option using a `not`, when the should not be present.

```yaml
- name: "Ensure /tmp/my.conf contains 127.0.0.1"
  ansible.builtin.lineinfile:
    path: /tmp/my.conf
    regexp: '^127\.0\.0\.1.*whatever'
    state: absent
  check_mode: yes
  register: out
  changed_when: false
  # failed_when: not out.found

- debug:
    msg: "Yes, line exists."
  when: out.found

- debug:
    msg: "Line does NOT exist."
  when: not out.found
```

See [this stackoverflow post](https://stackoverflow.com/questions/30786263/only-check-whether-a-line-present-in-a-file-ansible)
for a discussion.
