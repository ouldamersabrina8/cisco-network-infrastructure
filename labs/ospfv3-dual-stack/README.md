# Laboratoire OSPFv3 — Réseau Dual-Stack IPv4/IPv6

## 1. Présentation

Ce laboratoire a été réalisé dans le cadre de ma formation en gestion de réseaux et sécurité au Collège LaSalle.

Il porte sur la configuration du protocole de routage dynamique OSPFv3 dans une infrastructure Cisco utilisant simultanément IPv4 et IPv6 (Dual-Stack).

## 2. Objectifs

- Configurer l'adressage IPv4 et IPv6 sur les équipements réseau.
- Implémenter OSPFv3 avec les Address Families IPv4 et IPv6.
- Organiser le réseau en plusieurs zones OSPF, dont la zone backbone (Area 0).
- Configurer les identifiants Router ID.
- Vérifier les relations de voisinage OSPF et les routes apprises.
- Diagnostiquer les éventuels problèmes de connectivité.

## 3. Technologies utilisées

- Cisco IOS
- OSPFv3
- IPv4 / IPv6
- Address Families
- Routage multizone
- Interfaces Loopback
- Commandes de diagnostic Cisco

## 4. Vérification et dépannage

Les vérifications du laboratoire portent sur :

- L'établissement des voisinages OSPF.
- La présence des routes IPv4 et IPv6 dans les tables de routage.
- La connectivité entre les différents réseaux.
- La diffusion de la route par défaut, lorsqu'elle est configurée.

## 5. Documentation technique

Les schémas de topologie, configurations des équipements et captures des résultats seront ajoutés progressivement afin d'illustrer les étapes de configuration et de validation.

---

**Type de projet :** Laboratoire académique  
**Établissement :** Collège LaSalle — Montréal
## Dépannage et validation du routage OSPF

### 1. Présentation des travaux

Dans le cadre de mes laboratoires Cisco, j'ai configuré et vérifié des infrastructures utilisant OSPFv2 et OSPFv3, avec plusieurs zones de routage et une prise en charge des protocoles IPv4 et IPv6.

Ces travaux m'ont permis de développer mes compétences en configuration, en diagnostic et en résolution de problèmes de routage dynamique.

### 2. Configuration OSPFv3 Dual-Stack

J'ai mis en œuvre une infrastructure OSPFv3 multizone utilisant les Address Families IPv4 et IPv6.

Les principales opérations réalisées comprennent :

- Configuration des interfaces IPv4 et IPv6.
- Attribution des Router IDs.
- Configuration des zones OSPF 0, 1 et 2.
- Activation des Address Families IPv4 et IPv6.
- Vérification des relations de voisinage.
- Analyse des routes apprises dans les tables de routage.

### 3. Dépannage de la propagation de la route par défaut

**Objectif :** permettre aux routeurs internes d'apprendre une route par défaut à partir du routeur R2, utilisé pour simuler un accès vers un réseau externe.

**Problème rencontré :** la route par défaut n'était pas correctement propagée vers les autres équipements.

**Démarche de dépannage :**

- Vérification de la configuration des interfaces de R2.
- Vérification de la présence d'une route par défaut dans sa table de routage.
- Analyse de la configuration OSPF.
- Vérification de l'annonce de la route par défaut avec `default-information originate`.
- Contrôle des tables de routage des autres routeurs.

**Résultat :** après correction de la configuration, la route par défaut était visible sur les équipements concernés.

### 4. Vérification et diagnostic

Les commandes suivantes permettent de contrôler le fonctionnement du protocole OSPF selon la version et la plateforme Cisco utilisée :

```cisco
show ip ospf neighbor
show ip ospf interface brief
show ip route ospf
show ipv6 route ospf
show ospfv3 neighbor
show running-config
```

### 5. Compétences démontrées

- Configuration du routage dynamique OSPFv2 et OSPFv3.
- Administration d'une infrastructure multizone.
- Déploiement d'un réseau Dual-Stack IPv4/IPv6.
- Analyse des voisinages et des tables de routage.
- Diagnostic des problèmes de propagation des routes.
- Vérification et validation du fonctionnement réseau.

*Les topologies OSPFv2 et OSPFv3 proviennent de laboratoires distincts. Les captures de configuration et de validation seront ajoutées progressivement.*
