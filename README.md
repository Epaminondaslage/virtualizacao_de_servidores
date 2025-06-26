# Tecnologias de Virtualização


## 📑 Índice

1. [O que é Virtualização?](#o-que-é-virtualização)
2. [Tecnologias Comparadas](#tecnologias-comparadas)
3. [Tecnologias](#tecnologias)
    - [Proxmox VE](#proxmox-ve)
    - [VMware ESXi](#vmware-esxi)
    - [VMware Workstation](#vmware-workstation)
    - [VirtualBox](#virtualbox)
    - [Hyper-V](#hyper-v)
4. [Comparativo entre Tecnologias](#comparativo-entre-tecnologias)
5. [Benchmark entre tecnologias](https://github.com/Epaminondaslage/virtualizacao_de_servidores/blob/main/Benchmark.md)
6. [Comparativo: Máquinas Virtuais (VMs) x Contêineres LXC x Docker](https://github.com/Epaminondaslage/virtualizacao_de_servidores/blob/main/Comparativo_VMs_Conteiners.md)
7. [Instalação do Proxmox](https://github.com/Epaminondaslage/virtualizacao_de_servidores/blob/main/Install_Proxmox_VE.md)

## O que é Virtualização?

**Virtualização** é uma tecnologia que permite criar um ou mais ambientes computacionais isolados — chamados máquinas virtuais (VMs) — que simulam completamente o funcionamento de computadores físicos. Cada **VM** opera como se fosse um sistema independente, com seu próprio sistema operacional, aplicativos e recursos, mesmo estando todas hospedadas em um único hardware físico. Isso possibilita a execução simultânea de diferentes sistemas operacionais e cargas de trabalho de forma eficiente, segura e escalável.

---

## Tecnologias Comparadas

- **Proxmox VE**
- **VMware ESXi / Workstation**
- **VirtualBox**
- **Microsoft Hyper-V**

---

## Tecnologias

### **Proxmox VE**

**Proxmox VE (Virtual Environment)** é uma plataforma de virtualização open source baseada em Debian, que combina virtualização completa com **KVM** e conteinerização leve via **LXC**, oferecendo uma solução robusta para servidores, datacenters e ambientes de teste.

#### Principais Diferenciais:

- ✅ **Gerenciamento Web Intuitivo**  
  Interface gráfica acessível via navegador (`https://<IP>:8006`) que permite:
  - Criar, editar, iniciar e apagar VMs e containers
  - Visualizar uso de CPU, RAM e disco em tempo real
  - Agendar tarefas, configurar backups e atualizar o sistema

- 📦 **Suporte a KVM (Máquinas Virtuais) e LXC (Contêineres)**  
  - **KVM** (Kernel-based Virtual Machine): permite rodar sistemas operacionais completos (Linux, Windows, BSD etc.) com forte isolamento.
  - **LXC** (Linux Containers): mais leve, ideal para ambientes Linux onde performance e densidade são prioritárias.

- 🔗 **Clustering, Replicação e Backups Integrados**
  - **Cluster**: agrupe múltiplos servidores Proxmox para gerenciamento unificado.
  - **Replicação**: sincronização assíncrona de VMs entre nós do cluster (útil para alta disponibilidade).
  - **Backup**:
    - Suporte nativo a **backups completos e incrementais**.
    - Backups automáticos podem ser agendados pela interface.
    - Compatível com **Proxmox Backup Server**.

- 🧩 **Integração com Ceph e ZFS**
  - **Ceph**: sistema de armazenamento distribuído em cluster para alta disponibilidade e performance.
  - **ZFS**:
    - Sistema de arquivos com suporte a **snapshots**, **replicação**, **verificação de integridade** e **compressão**.
    - Ideal para ambientes que exigem confiabilidade e controle de armazenamento por volume.

> 🔗 Documentação oficial: [https://pve.proxmox.com/wiki/Main_Page](https://pve.proxmox.com/wiki/Main_Page)

---

### **VMware ESXi**

**VMware ESXi** é um hipervisor de tipo 1 (bare-metal) desenvolvido pela VMware, amplamente utilizado em ambientes corporativos e datacenters devido à sua alta estabilidade, desempenho e ampla gama de recursos empresariais.

#### Principais Diferenciais:

- ⚡ **Altíssimo Desempenho e Estabilidade**
  - Projetado para rodar diretamente no hardware físico, eliminando a necessidade de um sistema operacional host.
  - Utiliza um kernel proprietário altamente otimizado (VMkernel), garantindo desempenho e confiabilidade.
  - Amplamente validado em ambientes de missão crítica e infraestrutura de TI empresarial.

- 🔄 **Recursos Avançados Empresariais**
  - **vMotion**: migração ao vivo de máquinas virtuais entre hosts ESXi sem interrupção de serviço.
  - **vSAN (Virtual SAN)**: armazenamento definido por software integrado, com alta disponibilidade e performance.
  - **vSphere HA (High Availability)**: reinício automático de VMs em outro host em caso de falha.
  - **DRS (Distributed Resource Scheduler)**: balanceamento automático de carga entre hosts.

- 🔗 **Integração com vCenter Server**
  - Centraliza o gerenciamento de múltiplos hosts ESXi.
  - Permite gerenciamento avançado de clusters, agendamento de tarefas, monitoramento e automação.

- 🏢 **Adoção Corporativa**
  - Padrão de fato em virtualização empresarial.
  - Amplamente adotado por grandes empresas, provedores de nuvem e instituições financeiras.
  - Amplo suporte a hardware certificado (HCL: Hardware Compatibility List).

> 🔗 Documentação oficial: [https://docs.vmware.com/en/VMware-vSphere/index.html](https://docs.vmware.com/en/VMware-vSphere/index.html)

---

### **VMware Workstation**

**VMware Workstation** é um hipervisor de tipo 2 (hosted) voltado para desktops e estações de trabalho, ideal para desenvolvedores, testadores de software e profissionais de TI que precisam executar múltiplos sistemas operacionais simultaneamente em um único computador.

#### Principais Diferenciais:

- 🖥️ **Interface Gráfica Amigável**
  - Interface intuitiva com suporte a arrastar e soltar arquivos entre host e VM.
  - Facilidade na criação, clonagem e exportação de VMs.
  - Recursos avançados acessíveis via menus e configurações gráficas detalhadas.

- 🔄 **Integração com VMware ESXi e vCenter**
  - Suporte à conexão remota com hosts ESXi e vCenter.
  - Permite criar VMs localmente e migrá-las para servidores ESXi.
  - Compatibilidade com formatos de disco e snapshots do ecossistema VMware.

- 🌐 **Rede Virtual Avançada**
  - Criação de topologias de rede complexas com múltiplas interfaces e tipos:
    - NAT, Bridge, Host-only, LAN segment.
  - Ideal para simular ambientes corporativos, testes de firewall, VPN e containers em rede isolada.

- 🧪 **Ambiente de Testes Isolado e Flexível**
  - Suporte a snapshots, linked clones e gravação/reversão de estado.
  - Execução simultânea de diferentes sistemas operacionais para testes cruzados.
  - Compatível com recursos de virtualização aninhada (nested virtualization).

> 🔗 Documentação oficial: [https://www.vmware.com/products/workstation-pro.html](https://www.vmware.com/products/workstation-pro.html)


### **VirtualBox**

**VirtualBox** é um hipervisor de tipo 2 (hosted) de código aberto, desenvolvido pela Oracle, que permite executar diversos sistemas operacionais simultaneamente em uma máquina física. É amplamente utilizado em ambientes acadêmicos, laboratórios e por desenvolvedores, graças à sua simplicidade, portabilidade e custo zero.

#### Principais Diferenciais:

- 🧰 **Simples, Gratuito e Multiplataforma**
  - Compatível com Windows, Linux, macOS e Solaris.
  - Código aberto (sob licença GPLv2), com binários gratuitos para uso pessoal e educacional.
  - Instalação rápida e interface intuitiva para criação e gerenciamento de VMs.

- 🎓 **Ideal para Estudos e Desenvolvimento**
  - Ótima opção para aprendizado de sistemas operacionais, redes e testes de software.
  - Suporte a múltiplas VMs em paralelo, com controle total de recursos (CPU, RAM, disco, etc.).
  - Integração com extensões como VirtualBox Guest Additions, oferecendo melhor desempenho gráfico e funcionalidades extras dentro da VM.

- 🌐 **Recursos de Rede Flexíveis**
  - Suporte a modos de rede:
    - **NAT**: permite acesso à internet via rede do host.
    - **Bridge**: conecta a VM diretamente à rede física.
    - **Host-only**: comunicação entre host e VM sem acesso externo.
    - **Internal Network**: comunicação isolada entre VMs.
  - Perfeito para testes de servidores, simulações de redes e ambientes de laboratório.

- 💾 **Recursos Adicionais**
  - **Snapshots**: salvar e restaurar estados da VM com facilidade.
  - **Clone de VMs**: criar cópias completas ou ligadas de máquinas virtuais.
  - Suporte a virtualização aninhada e múltiplos sistemas de arquivos de disco virtual (VDI, VMDK, VHD, etc.).

> 🔗 Documentação oficial: [https://www.virtualbox.org/manual/](https://www.virtualbox.org/manual/)


### **Hyper-V**

**Hyper-V** é o hipervisor de virtualização da Microsoft, integrado ao Windows nas versões Pro, Enterprise e Server. Ele permite criar e gerenciar máquinas virtuais de forma nativa em sistemas Windows, sendo uma solução sólida para ambientes corporativos, especialmente aqueles integrados ao Active Directory.

#### Principais Diferenciais:

- 🔗 **Integração com Windows e Active Directory**
  - Gerenciamento direto via ferramentas do Windows como Hyper-V Manager, PowerShell e Windows Admin Center.
  - Integra-se facilmente a domínios do Active Directory, facilitando políticas de segurança, permissões e gerenciamento centralizado.

- 🔁 **Suporte a Virtualização Aninhada (Nested)**
  - Permite executar máquinas virtuais **dentro de outras VMs**, útil para cenários de laboratório, testes de hipervisores e DevOps.
  - Ideal para ambientes de desenvolvimento e testes que simulam estruturas completas de datacenter.

- 🏢 **Foco em Ambientes Microsoft**
  - Compatibilidade total com sistemas Windows Server e clientes Windows.
  - Suporte nativo a formatos de disco **VHD/VHDX**, Live Migration, checkpoints (snapshots) e gerenciamento remoto.
  - Funcionalidade de **replicação de VMs (Hyper-V Replica)** para recuperação de desastres.

- 🧰 **Gerenciamento e Ferramentas**
  - Interface gráfica (Hyper-V Manager) e suporte total via **PowerShell**.
  - Gerenciamento remoto via **Windows Admin Center** ou System Center.
  - Ferramentas de integração instaladas nas VMs melhoram desempenho e comunicação com o host.

> 🔗 Documentação oficial: [https://learn.microsoft.com/en-us/virtualization/hyper-v-on-windows/](https://learn.microsoft.com/en-us/virtualization/hyper-v-on-windows/)

---

## Comparativo entre tecnologias

| Recurso / Tecnologia     | Proxmox VE                     | VMware ESXi                 | VMware Workstation         | VirtualBox                     | Hyper-V                          |
|--------------------------|--------------------------------|-----------------------------|-----------------------------|----------------------------------|----------------------------------|
| **Tipo de Hipervisor**   | Tipo 1 (bare-metal)            | Tipo 1 (bare-metal)         | Tipo 2 (hosted)             | Tipo 2 (hosted)                  | Tipo 1 (bare-metal) ou Tipo 2    |
| **Base do Sistema**      | Debian Linux                   | Kernel ESXi próprio         | Roda sobre Windows/Linux    | Roda sobre Windows/Linux/macOS  | Roda sobre Windows               |
| **Interface de Gerência**| Interface Web + CLI (shell)    | Interface Web (vSphere)     | Interface gráfica (GUI)     | Interface gráfica (GUI)         | GUI no Windows / PowerShell      |
| **Gerenciamento Remoto** | Sim (via navegador)            | Sim (via vSphere)           | Sim (com Workstation Pro)   | Não nativamente                 | Sim (via Remote Manager)         |
| **Recursos Avançados**   | Snapshots, LXC, Cluster, HA    | Snapshots, vMotion, HA      | Snapshots, redes virtuais   | Snapshots, redes NAT/Bridge     | Snapshots, Live Migration (Server) |
| **Containers**           | Sim (LXC)                      | Não                         | Não                         | Não                              | Parcial (Windows Server)         |
| **Compatibilidade SO**   | Linux, Windows, BSD, etc.      | Linux, Windows, BSD, etc.   | Linux, Windows, BSD, etc.   | Linux, Windows, BSD, etc.       | Principalmente Windows/Linux     |
| **Uso de Recursos**      | Baixo a moderado               | Muito leve e otimizado      | Moderado a alto             | Baixo a moderado                | Moderado                         |
| **Instalação**           | Instalação direta via ISO      | Instalação direta via ISO   | Instalação como programa    | Instalação como programa        | Ativado no Windows (Pro/Server)  |
| **Gratuito?**            | Sim (100% funcional)           | Gratuito com limitações     | Não (licença paga)          | Sim (open-source)               | Sim (nas edições compatíveis)    |
| **Licenciamento**        | Open Source (AGPLv3)           | Proprietário (VMware)       | Proprietário (VMware)       | Open Source (GPL)               | Proprietário (Microsoft)         |
| **Ideal para**           | Servidores, laboratórios, clusters | Empresas, datacenters       | Estações de trabalho        | Estudantes, testes e devs       | Ambientes Microsoft corporativos |

### Resumo:

- **Proxmox VE**: melhor escolha para servidores e laboratórios.
- **VMware ESXi**: padrão ouro corporativo, mas requer licenças.
- **VMware Workstation**: ótimo para desenvolvedores, mas é pago.
- **VirtualBox**: ideal para iniciantes, estudantes e testes rápidos.


