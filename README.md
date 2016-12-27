<p align="right">
    <a href="https://travis-ci.org/epiloque/ansible-duo_unix">
        <img src="https://travis-ci.org/epiloque/ansible-duo_unix.svg?branch=master"
             alt="build status">
    </a>
        <a href="https://galaxy.ansible.com/epiloque/duo_unix">
        <img src="https://img.shields.io/badge/ansible--galaxy-duo_unix-blue.svg"
             alt="ansible galaxy">
    </a>
</p>

duo_unix role

## Role Variables

Available variables are listed below, along with default values:

```yaml
# Duo Security integration key
duo_unix_duo_ikey:

# Duo Security secret key
duo_unix_duo_skey:

# Duo Security API hostname (i.e. api-XXXXXXXX.duosecurity.com
duo_unix_duo_host:

# If specified, Duo authentication is required only for users whose primary group
# or supplementary group list matches one of the space-separated pattern lists.
#
# A pattern consists of zero or more non-whitespace characters, "*" (a wild card
# that matches zero or more characters), or "?" (a wildcard that matches exactly
# one character).
#
# A pattern-list is a comma-separated list of patterns. Patterns within
# pattern-lists may be negated by preceding them with an exclamation mark ("!").
# For example, to specify Duo authentication for all users (except those that are
# also admins), and for guests:
dup_unix_groups:

# Include information such as the command to be executed in the Duo Push message.
# Either "yes" or "no". The default is "no".
duo_unix_duo_pushinfo: no

# On service or configuration errors that prevent Duo authentication, fail "safe"
# (allow access) or "secure" (deny access).
duo_unix_duo_failmode: secure

# If a user fails to authenticate with a second factor, Duo Unix will prompt the
# user to authenticate again. This option sets the maximum number of prompts that
# Duo Unix will display before denying access. Must be 1, 2, or 3. Default is 3.
#
# For example, when prompts = 1, the user will have to successfully authenticate
# on the first prompt, whereas if prompts = 2, if the user enters incorrect
# information at the initial prompt, he/she will be prompted to authenticate
# again.
duo_unix_duo_prompts: 3

# Either "yes" or "no". Default is "no". If "yes", Duo Unix will automatically
# send a push login request to the user's phone, falling back on a phone call if
# push is unavailable. If "no", the user will be prompted to choose an
# authentication method.  When configured with autopush = yes, we recommend
# setting prompts = 1.
duo_unix_autopush: no
```

## Example Playbook

```yaml
- hosts: servers
  vars:
    duo_unix_duo_ikey: integration-key
    duo_unix_duo_skey: secret-key
    duo_unix_duo_host: api-xxxxxx.duosecurity.com
  roles:
    - epiloque.duo_unix
```

## License

BSD
