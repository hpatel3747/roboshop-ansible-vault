### roboshop-ansible-vault is ansible to query vault for pwds and parameter values

#### pre-requisite to lookup hashi vault

- hvac python library is required
- Install hvac 
```text
pip install hvac
```
### Examples
```text

- ansible.builtin.debug:
  msg: "{{ lookup('community.hashi_vault.hashi_vault', 'secret=secret/hello:value token=c975b780-d1be-8016-866b-01d0f9b688a5 url=http://myvault:8200') }}"

# retrieve url:
{{ lookup('hashi_vault', 'roboshop-{{env}}/data/frontend:catalogue_url token={{ vault_token }} url=http://vault-internal.hptldevops.online:8200')}}; }

# retrieve pwd
{{ lookup('hashi_vault', 'roboshop-{{env}}/data/mysql:mysql_root_password token={{ vault_token }} url=http://vault-internal.hptldevops.online:8200')}}

- name: Return all secrets from a path
  ansible.builtin.debug:
  msg: "{{ lookup('community.hashi_vault.hashi_vault', 'secret=secret/hello token=c975b780-d1be-8016-866b-01d0f9b688a5 url=http://myvault:8200') }}"
```
