# 📦 Instalação Detalhada do Proxmox VE do Zero

Este guia descreve detalhadamente como instalar o Proxmox VE (Virtual Environment) em um servidor físico ou máquina dedicada.

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

---

## 💿 Passo 2: Criar Pendrive Bootável

### No Windows:
- Use o **Rufus**: https://rufus.ie

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
4. Defina:
   - Idioma e teclado
   - Senha do usuário `root`
   - E-mail do administrador
   - Hostname (ex: `proxmox.local`)
   - IP fixo (recomendado), gateway, e DNS
5. Clique em **Install** e aguarde a conclusão
6. Após a instalação, o sistema reiniciará

---

## 🌐 Passo 5: Acessar a Interface Web

No navegador de outro computador da rede, acesse:

```
https://<IP_do_Proxmox>:8006
```

Exemplo:
```
https://192.168.1.100:8006
```

> Ignore o aviso de certificado SSL inválido.

---

## 🔐 Passo 6: Login

- Usuário: `root`
- Senha: (aquela que foi definida)
- Realm: `Linux PAM`

---

## 🛠️ Passo 7: Pós-instalação

### Atualizar o sistema:
```bash
apt update && apt full-upgrade -y
```

### Criar sua primeira VM:
1. Vá em “Create VM”
2. Dê um nome
3. Selecione uma imagem ISO
4. Configure CPU, RAM, disco e rede
5. Inicie a VM e instale o sistema operacional desejado

---

## 💾 Backup e Manutenção

- Proxmox possui sistema de backup embutido.
- Use snapshots para salvar o estado das VMs antes de atualizações.
- Agende backups automáticos via interface web.

---
