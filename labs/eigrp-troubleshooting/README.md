# Dépannage et résolution d'incidents EIGRP — Cisco

## Présentation

Ce laboratoire présente plusieurs scénarios de dépannage du protocole EIGRP, réalisés dans un environnement Cisco simulé.

L'objectif était d'identifier les anomalies de configuration empêchant l'établissement des voisinages ou la propagation correcte des routes, puis de rétablir le fonctionnement du réseau.

## Environnement technique

- Équipements Cisco : routeurs R1, R2 et R3
- Protocole : EIGRP pour IPv4
- Système autonome : AS 10
- Réseaux de transit : 10.0.0.0/30 et 10.0.0.4/30
- Réseaux locaux : 192.168.10.0/24, 192.168.20.0/24 et 192.168.30.0/24

## Scénario 1 — Problème d'authentification EIGRP

**Symptôme :** les routeurs ne parvenaient pas à établir correctement leur voisinage EIGRP.

**Diagnostic :** vérification des chaînes de clés et des paramètres d'authentification configurés sur les interfaces.

**Cause identifiée :** incohérence entre les paramètres d'authentification, notamment le nom de la chaîne de clés ou la valeur de la clé.

**Correction :** harmonisation des paramètres d'authentification sur les interfaces concernées.

**Vérification :** contrôle du voisinage EIGRP après correction.

## Scénario 2 — Interface passive

**Symptôme :** une relation de voisinage EIGRP attendue n'était pas établie.

**Cause identifiée :** l'interface GigabitEthernet0/0 de R1 était configurée comme interface passive.

**Correction :**

```cisco
router eigrp 10
 no passive-interface GigabitEthernet0/0
```

Cette correction permet de réactiver l'envoi des messages Hello EIGRP sur l'interface concernée.

## Scénario 3 — Masque de sous-réseau incorrect

**Symptôme :** problème de cohérence d'adressage sur une liaison entre routeurs.

**Cause identifiée :** l'interface GigabitEthernet0/1 de R3 utilisait un masque `/16` au lieu du masque `/30` prévu.

**Correction :** modification du masque en `255.255.255.252`, conformément au plan d'adressage du laboratoire.

## Scénario 4 — Liste de contrôle d'accès (ACL)

**Symptôme :** une configuration ACL perturbait le fonctionnement réseau attendu.

**Diagnostic :** examen de l'ACL 10 appliquée en entrée sur l'interface GigabitEthernet0/1 de R2.

**Correction :** retrait de l'ACL de l'interface dans le cadre du scénario de dépannage.

**Vérification :** contrôle de la table de routage EIGRP après correction.

## Vérifications techniques

Les principales commandes de diagnostic utilisées dans ces scénarios comprennent :

```cisco
show ip eigrp neighbors
show ip route eigrp
show ip protocols
show ip interface
show access-lists
show running-config
```

Les vérifications ont notamment permis de confirmer sur R1 la présence d'une route EIGRP vers le réseau `192.168.30.0/24` via `10.0.0.2`.

## Compétences démontrées

- Diagnostic des problèmes de voisinage EIGRP
- Dépannage de l'authentification réseau
- Analyse des interfaces passives
- Vérification de l'adressage IP et des masques
- Analyse des listes de contrôle d'accès
- Vérification des tables de routage
- Résolution méthodique des incidents réseau

## Documentation

Les captures de topologie, les configurations et les résultats des commandes de vérification pourront être ajoutés pour illustrer les scénarios.

---

**Contexte :** Travaux pratiques de dépannage Cisco réalisés dans le cadre de ma formation en gestion de réseaux et sécurité.
