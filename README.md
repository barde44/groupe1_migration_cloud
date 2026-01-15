# Démo : Automatisation de serveurs Web avec Ansible

Ce projet démontre l'utilisation d'**Ansible** pour le déploiement automatisé et simultané d'une infrastructure Web sur un parc de serveurs Linux (Debian).

## Présentation du Projet
L'objectif est de transformer deux machines vierges en serveurs Web fonctionnels en une seule commande, sans intervention manuelle sur les machines cibles. Ce projet illustre les concepts d'**Infrastructure as Code (IaC)** et d'**Idempotence**.



## Architecture de la Démo
* **Contrôleur (Maître) :** Ubuntu Desktop
* **Cibles (Nodes) :** * `Debian-1` (IP: 192.168.61.155)
    * `Debian-2` (IP: 192.168.61.156)
* **Protocole :** SSH (Authentification par clé publique)
* **Services installés :** Nginx, Configuration HTML/CSS personnalisée.

---

## Structure du Répertoire
```plaintext
demo/
├── hosts.ini           # Inventaire des machines cibles
├── playbook.yml        # Script d'automatisation (recette)
├── website/            # Dossier contenant les sources du site
│   └── index.html      # Page d'accueil personnalisée
└── README.md           # Documentation du projet

## Guide d'utilisation

### 1. Prérequis
Ansible installé sur la machine de contrôle.

Accès SSH configuré vers les cibles (ssh-copy-id).

L'utilisateur sur les cibles doit avoir les droits sudo.

### 2. Vérification de la connectivité
Avant le déploiement, vérifier que les cibles sont joignables :
`Bash
ansible webservers -i hosts.ini -m ping`

### 3. Exécution du déploiement
Lancer le playbook pour configurer l'ensemble du parc :
`Bash
ansible-playbook -i hosts.ini playbook.yml -K`

## Concepts Clés démontrés
Inventaire Groupé : Gestion de plusieurs serveurs simultanément via le groupe [webservers].

Gestion des fichiers : Utilisation du module copy pour synchroniser un dossier local vers des serveurs distants.

Idempotence : Le playbook peut être relancé plusieurs fois ; Ansible ne modifiera le serveur que si l'état actuel diffère de l'état souhaité (ex: modification du code HTML).

Mode Become : Élévation de privilèges (sudo) gérée de manière sécurisée durant l'exécution.

### Équipe du Projet (Groupe 1) : 

ASSIH Esso Mèwè Jacques 
BARDE Steven 
JOHNSON Bèni Jeff 
KEGDIGOMA Ditoma 
IKPAGNATE Kodjo 
TEPE Paulin 

Examinateur : M. WOAGOU