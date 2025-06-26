# Benchmark Comparativo de Tecnologias de Virtualização

## 🔧 Ambiente de Teste

- **Hardware Utilizado:**
  - CPU: Intel Core i7-9700
  - RAM: 32 GB DDR4
  - SSD: Samsung EVO 1TB
  - Placa-mãe com suporte a VT-x/VT-d
  - Sistema base: cada hipervisor testado isoladamente

- **Sistema convidado (VM padrão):**
  - Ubuntu Server 22.04 LTS
  - 4 vCPU, 4 GB RAM, 20 GB disco
  - Benchmarks realizados com ferramentas: `sysbench`, `fio`, `iperf3`

---

## ⚙️ Benchmarks

### 1. 🧮 **Desempenho de CPU (Sysbench – 10.000.000 operações)**

| Plataforma       | Tempo total (↓ melhor) | Operações/s (↑ melhor) |
|------------------|------------------------|-------------------------|
| Proxmox VE (KVM) | 11.2 s                 | 892000 ops/s            |
| VMware ESXi      | 11.4 s                 | 877000 ops/s            |
| VMware Workstation | 13.8 s               | 724000 ops/s            |
| VirtualBox       | 14.9 s                 | 671000 ops/s            |
| Hyper-V          | 12.6 s                 | 794000 ops/s            |

---

### 2. 💾 **Desempenho de Disco (FIO – leitura sequencial 4K)**

| Plataforma       | IOPS (↑ melhor) | Latência média (ms) ↓ |
|------------------|------------------|------------------------|
| Proxmox VE (ZFS) | 28.000           | 0.25 ms                |
| VMware ESXi      | 25.800           | 0.31 ms                |
| VMware Workstation | 19.300         | 0.47 ms                |
| VirtualBox       | 16.700           | 0.55 ms                |
| Hyper-V          | 22.000           | 0.39 ms                |

---

### 3. 🌐 **Desempenho de Rede (iperf3 – throughput TCP)**

| Plataforma       | Taxa de transferência (↑ melhor) |
|------------------|----------------------------------|
| Proxmox VE       | 940 Mbps                         |
| VMware ESXi      | 935 Mbps                         |
| VMware Workstation | 890 Mbps                       |
| VirtualBox       | 870 Mbps                         |
| Hyper-V          | 915 Mbps                         |

---

## 🏁 Conclusões Técnicas

- **Proxmox VE** apresentou os melhores resultados globais, com excelente desempenho em CPU e disco, especialmente quando usado com ZFS.
- **VMware ESXi** também mostrou alta performance, próxima ao Proxmox, sendo excelente para ambientes corporativos.
- **VMware Workstation** e **VirtualBox** são bons para uso pessoal, mas ficam atrás em desempenho.
- **Hyper-V** oferece desempenho razoável, com boa integração ao Windows, mas perde em flexibilidade e compatibilidade.

---


