# Ansible Role Development

## Prerequisites

*   Python3
*   [Podman](https://podman.io/)

## Setup

*   Create a [Virtual Environment](https://docs.python.org/3/tutorial/venv.html) and install modules
*   Use [Molecule](https://molecule.readthedocs.io) to initialise the role using the Podman driver

```bash
python -m venv .venv
source .venv/bin/activate
pip install --upgrade pip
pip install -r requirements.txt
```

```bash
molecule init role -d podman japeoh.role-name
```

## Molecule Podman Issues

Currently there is a [bug](https://github.com/ansible-community/molecule/issues/2585) that requires pipelining in 
the Molecule provisioner to be disabled.

```bash
sed -i 's/"pipelining": True,/"pipelining": False,/g' .venv/lib/python3.7/site-packages/molecule/provisioner/ansible.py
```
