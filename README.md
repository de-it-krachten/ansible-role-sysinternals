[![CI](https://github.com/de-it-krachten/ansible-role-sysinternals/workflows/CI/badge.svg?event=push)](https://github.com/de-it-krachten/ansible-role-sysinternals/actions?query=workflow%3ACI)


# ansible-role-sysinternals

<basic role description>



## Dependencies

#### Roles
None

#### Collections
- ansible.windows
- community.windows

## Platforms

Supported platforms

- Windows Server 2012 R2<sup>1</sup>
- Windows Server 2016<sup>1</sup>
- Windows Server 2019<sup>1</sup>
- Windows Server 2022<sup>1</sup>
- Windows Server 2025<sup>1</sup>

Note:
<sup>1</sup> : no automated testing is performed on these platforms


## Role Variables
### defaults/main.yml
<pre><code>
# Location where to install sysinternals to
sysinternals_install_root: 'c:\windows\temp'

# Dict of diffeent sysinternal tools supported
sysinternals_tools_info:
  pendmoves:
    name: pendmoves
    url: https://download.sysinternals.com/files/pendmoves.zip
    exe: pendmoves.exe
  handle:
    name: handle
    url: https://download.sysinternals.com/files/Handle.zip
    exe: handle.exe
  tcpview:
    name: tcpview
    url: https://download.sysinternals.com/files/TCPView.zip
    exe: tcpview.exe

# List of sysinternal tools created from dict above
sysinternals_tools: "{{ sysinternals_tools_info | dict2items | json_query('[].key') }}"
</pre></code>




## Example Playbook
### molecule/default/converge.yml
<pre><code>
- name: sample playbook for role 'sysinternals'
  hosts: all
  become: 'yes'
  tasks:
    - name: Include role 'sysinternals'
      ansible.builtin.include_role:
        name: sysinternals
</pre></code>
