## Rchain Ansible

This is an ansible repo to setup and run an rchain node against a testnet.

## Installing Ansible

Check the [official docs](http://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#installing-the-control-machine) for installing on the control machine.

## Configuration

- Update `inventory` with your server IP

- Update the environment vars in `group_vars/rchain-node.yml` for your own settings

### SSH

When you first attempt to run an ansible playbook, it needs to be able to SSH to the target machine in the same way that you would manually SSH via the command line.

Set up key based authentication for SSH, and update the `ansible_user` variable in `group_vars/rchain-node.yml` with that user.

### Ansible Commands

Install rchain on a fresh server:

```
ansible-playbook rchain.yml -e "host=rchain-node"
```

Install a testnet:

```
ansible-playbook testnet.yml -e "host=rchain-node"
```

Update a config file:

```
ansible-playbook testnet.yml -e "host=rchain-node" --tags=config
```

### Raw Commands

Create a move in tic tac toe:

```
rnode deploy contracts/ticTacToe.rho
```

Action the moves:

```
rnode propose
```

Find the peer count:

```
curl -s localhost:40403 | grep -A 1 "peers gauge"
```

Get the blocks:

```
rnode show-blocks
```

Get dianostics

```
rnode diagnostics
```
