# 📦 VM DATAMANAGEMENT - VM D'ADMINISTRATION 

` Avoir un environnement nous permettant l'administration et la supervision de l'ensemble de l'infrastructure `


## 🧱 Fondation de l'infrastructure

🔹 OS : Debian
Rôle : Système d'exploitation stable et sécurisé pour serveurs.

Intérêt : Debian est réputé pour sa robustesse, son cycle de mises à jour long et sa compatibilité avec la majorité des outils open source. Base idéale pour les serveurs de production.

🔹 Docker
Rôle : Conteneurisation des applications.

Intérêt : Isoler les services dans des conteneurs légers, faciliter le déploiement, la scalabilité, la portabilité et les mises à jour (grâce aux images). Facilite la gestion et l'automatisation des stacks.

## 🖥️ Services de supervision et d’observabilité

### 🔹 Grafana
Rôle : Interface de visualisation de données.

Intérêt : Permet de créer des tableaux de bord pour surveiller les métriques système, réseau, logs, etc. Lecture des données de Prometheus ou Loki.

### 🔹 Prometheus
Rôle : Collecte de métriques et monitoring.

Intérêt : Scrape les données de performance des services (CPU, mémoire, temps de réponse...). Idéal pour l’alerte et le suivi d'état système.

### 🔹 Loki
Rôle : Agrégation de logs (comme ELK, mais plus léger).

Intérêt : Centralise les logs de tous les conteneurs/services. Conçu pour s’intégrer parfaitement avec Grafana.

### 🔹 Promtail
Rôle : Collecte de logs depuis les conteneurs/serveurs vers Loki.

Intérêt : Agent léger installé sur chaque machine (ou conteneur) pour pousser les logs vers Loki.

### 📥 Gestion de tickets et d’inventaire
🔹 GLPI
Rôle : ITSM (gestion de parc, tickets, incidents).

Intérêt : Suivi des tickets utilisateurs, gestion des incidents, des demandes, du matériel et des logiciels. Utile pour les équipes support.

🔐 Accès, sécurité et connectivité
🔹 Tailscale
Rôle : VPN maillé Zero-Config basé sur WireGuard.

Intérêt : Connecte facilement et de manière sécurisée plusieurs nœuds via un VPN privé, sans config réseau complexe. Idéal pour accès distant au serveur sans exposer de ports publics.

🔹 Fail2ban
Rôle : Sécurité contre les attaques brute-force.

Intérêt : Analyse les logs, bannit les IP suspectes automatiquement (SSH, Apache, etc.). Renforce la sécurité du serveur.

🧩 Infrastructure réseau et base de données
🔹 MariaDB
Rôle : Base de données relationnelle.

Intérêt : Fournit le backend de stockage pour GLPI, Grafana, etc. Compatible avec MySQL, performant et open source.

🔹 Cloudflared
Rôle : Tunnel sécurisé vers Cloudflare (proxy reverse).

Intérêt : Expose des services locaux (ex : panel GLPI) via HTTPS avec protection DDoS, sans ouverture de ports, grâce à Cloudflare Tunnel.

🔹 Apache2
Rôle : Serveur web / Reverse Proxy.

Intérêt : Permet d'exposer proprement les services Docker via des sous-domaines, d’ajouter SSL, redirections, headers, etc. Peut être remplacé par Nginx selon les cas.

⚙️ Interface d’administration
🔹 Portainer
Rôle : Interface graphique de gestion Docker.

Intérêt : Permet d’administrer tous les conteneurs, stacks, volumes, images, réseaux… sans ligne de commande. Idéal pour l’observation rapide et la gestion simplifiée.