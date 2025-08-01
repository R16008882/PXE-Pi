# 🖥️ Serveur PXE sur Raspberry Pi 3 B+

Ce projet configure un **Raspberry Pi 3 B+** comme serveur PXE complet, permettant le démarrage réseau (PXE boot) de machines BIOS et UEFI pour installer Ubuntu ou charger un système Yocto via NFS.

## 🎯 Objectifs
- Automatiser le déploiement de systèmes d'exploitation.
- Supporter à la fois le boot **BIOS (PXELINUX)** et **UEFI (GRUB)**.
- Héberger une image Ubuntu Server et un rootfs Yocto.
- Servir de plateforme de test pour des images embarquées (Yocto → Docker).

## 🛠️ Stack technique
- **Matériel** : Raspberry Pi 3 B+
- **OS** : Linux (Raspberry Pi OS)
- **Services** :
  - DHCP (`isc-dhcp-server`)
  - TFTP (`tftpd-hpa`)
  - HTTP (`apache2`)
  - NFS (pour Yocto rootfs)
- **Bootloaders** : SYSLINUX (BIOS), GRUB UEFI (signed)
- **Images** : Ubuntu 22.04 Live Server, Yocto (custom)

## 📦 Fonctionnalités
- [x] Configuration IP statique
- [x] Serveur DHCP avec redirection PXE
- [x] Serveur TFTP avec chargeurs d'amorçage
- [x] Menu GRUB pour UEFI (Ubuntu / Yocto)
- [x] Support PXELINUX pour BIOS
- [x] Téléchargement et montage ISO Ubuntu
- [x] Chargement Yocto via NFS root

## 🧪 Usage
1. Connecte un client en réseau avec boot PXE activé (BIOS ou UEFI).
2. Le client obtient une IP via DHCP.
3. Il télécharge le bootloader via TFTP.
4. Menu GRUB ou PXELINUX affiché → choix du système.

## 🖼️ Schéma d'architecture
![PXE Architecture](docs/architecture_diagram.png)

## 🔐 Sécurité
- Permissions TFTP corrigées (`755` au lieu de `777`)
- Réseau isolé recommandé pour usage en production

## 📚 Liens utiles
- [Tutoriel original (YouTube)](https://www.youtube.com/watch?v=_IgCtgHID1Y)
- [Documentation ISC DHCP](https://www.isc.org/software/dhcp)
