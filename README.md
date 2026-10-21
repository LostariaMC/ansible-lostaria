# ansible-lostaria

Gestion des utilisateurs et de leurs clés SSH sur les serveurs

- `playbook.yml` : crée les users et pose les clés
- `data/` : submodule `ansible-lostaria-inventory`
  - `inventory.ini` : les serveurs
  - `users.yml` : les utilisateurs et leurs clés SSH

## Installation

Cloner le submodule de l'inventaire en amont : `ansible-lostaria-inventory`

Initialiser l'inventaire (au premier clone)
```bash
git submodule update --init
```

Récupérer la dernière version de l'inventaire
```bash
git submodule update --remote
```

```bash
ansible-galaxy collection install ansible.posix
```

## Utilisation

Voir ce qui va changer, sans rien modifier
```bash
ansible-playbook playbook.yml -u root --check --diff
```

```bash
ansible-playbook playbook.yml -u root
```

Déployer sur un seul serveur
```bash
ansible-playbook playbook.yml -u root --limit server1
```
