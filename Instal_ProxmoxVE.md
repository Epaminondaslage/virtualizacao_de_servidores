![logo_proxmox.png](logo_proxmox.png)

# 📦 Instalação do Proxmox VE

Guia simplificado para instalar e configurar o Proxmox VE em um servidor físico ou máquina dedicada, incluindo criação de VMs, containers LXC e configuração de rede com IP fixo.

---

## 📑 Índice

1. [Requisitos Mínimos](#-requisitos-mínimos)
2. [Baixar o Proxmox](#-passo-1-baixar-o-proxmox)
3. [Criar Pendrive Bootável](#-passo-2-criar-pendrive-bootável)
4. [Boot pela Mídia](#-passo-3-boot-pela-mídia)
5. [Instalar o Proxmox VE](#-passo-4-instalar-o-proxmox-ve)
6. [Acessar a Interface Web](#-passo-5-acessar-a-interface-web)
7. [Login](#-passo-6-login)
8. [Pós-instalação](#-passo-7-pós-instalação)
9. [Backup e Manutenção](#-backup-e-manutenção)
10. [Comandos no Proxmox](#-comandos-no-proxmox)
11. [Criar Container LXC](#-criar-um-container-lxc-no-proxmox-via-terminal)
12. [Criar Container com IP Fixo](#-criar-containers-lxc-com-ip-fixo-no-proxmox)

---

## 🧰 Requisitos Mínimos

- CPU com suporte a Intel VT-x ou AMD-V
- 4 GB de RAM (recomendado 8 GB ou mais)
- SSD ou HDD com pelo menos 32 GB livres
- Conexão de rede cabeada
- Pendrive de 2 GB ou mais

---

## 🔽 Passo 1: Baixar o Proxmox

1. Acesse: [https://www.proxmox.com/en/downloads](https://www.proxmox.com/en/downloads)
2. Baixe a ISO do Proxmox VE (ex: `proxmox-ve_8.x.iso`)

[Documentação oficial Proxmox - Downloads](https://pve.proxmox.com/wiki/Downloads)

---

## 💿 Passo 2: Criar Pendrive Bootável

### No Windows:
- Use o **Rufus**: [https://rufus.ie](https://rufus.ie)

### No Linux/macOS:
```bash
sudo dd if=proxmox-ve_8.x.iso of=/dev/sdX bs=4M status=progress
```
> Substitua `sdX` pelo seu dispositivo USB correto.

---

## ⚙️ Passo 3: Boot pela Mídia

1. Insira o pendrive no servidor.
2. Ligue o equipamento e entre no menu de boot (F12, DEL, ESC…).
3. Escolha o pendrive e inicie o instalador.

---

## 🧰 Passo 4: Instalar o Proxmox VE

1. Selecione “Install Proxmox VE”
2. Aceite os termos de uso
3. Escolha o disco onde o sistema será instalado
4. Configure idioma, teclado, senha do `root`, e-mail e IP fixo
5. Clique em **Install** e aguarde

[Instalação passo a passo - Proxmox Wiki](https://pve.proxmox.com/wiki/Installation)

---

## 🌐 Passo 5: Acessar a Interface Web

Acesse pelo navegador:

```
https://<IP_do_Proxmox>:8006
```

> Ignore o aviso de certificado SSL inválido.

---

## 🔐 Passo 6: Login

- Usuário: `root`
- Senha: (definida na instalação)
- Realm: `Linux PAM`

---

## 🛠️ Passo 7: Pós-instalação

Atualize o sistema:
```bash
apt update && apt full-upgrade -y
```

---

## 💾 Backup e Manutenção

- Use snapshots para segurança
- Agende backups automáticos via interface web

[Guia de backup no Proxmox](https://pve.proxmox.com/wiki/Backup_and_Restore)

---

## ⚙️ Comandos no Proxmox

### Criar VM via terminal

```bash
qm create 100 --name vm-ubuntu --memory 2048 --net0 virtio,bridge=vmbr0
qm importdisk 100 ubuntu22.qcow2 local-lvm
qm set 100 --scsihw virtio-scsi-pci --scsi0 local-lvm:vm-100-disk-0
qm set 100 --boot c --bootdisk scsi0
qm start 100
```

[Documentação de VMs - Proxmox](https://pve.proxmox.com/wiki/VM_Management)

---

## 📦 Criar um Container LXC no Proxmox (via terminal)

```bash
pct create 101 local:vztmpl/debian-11-standard_11.6-1_amd64.tar.zst --hostname container-debian --cores 2 --memory 1024 --rootfs local-lvm:8 --net0 name=eth0,bridge=vmbr0,ip=dhcp --start 1
```

[Documentação oficial de LXC no Proxmox](https://pve.proxmox.com/wiki/Linux_Container)

---

## 🌐 Criar Containers LXC com IP Fixo no Proxmox

```bash
pct create 102 local:vztmpl/debian-11-standard_11.6-1_amd64.tar.zst --hostname container-fixo --cores 2 --memory 1024 --rootfs local-lvm:8 --net0 name=eth0,bridge=vmbr0,ip=192.168.1.50/24,gw=192.168.1.1 --start 1
```

Após criação, edite:
```bash
nano /etc/network/interfaces
```

Exemplo:
```text
auto eth0
iface eth0 inet static
    address 192.168.1.50
    netmask 255.255.255.0
    gateway 192.168.1.1
```

Reinicie a rede:
```bash
systemctl restart networking
```

Verifique IP:
```bash
ip a
```

[Configuração de rede - LXC Debian](https://wiki.debian.org/NetworkConfiguration)

---
