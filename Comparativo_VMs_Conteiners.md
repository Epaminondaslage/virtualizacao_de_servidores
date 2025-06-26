# Comparativo: Máquinas Virtuais (VMs) x Contêineres LXC x Docker

Comparação entre as principais tecnologias de virtualização e conteinerização, com foco em desempenho, isolamento, uso de recursos e casos de uso.

---

## 🧩 Conceitos

### 🖥️ Máquinas Virtuais (VMs)

Máquinas virtuais são ambientes completos que simulam todo o hardware de um computador físico. Cada VM roda seu próprio sistema operacional (chamado de "convidado") de forma totalmente isolada do sistema anfitrião. Para isso, utilizam um **hipervisor**, que pode ser do tipo 1 (bare-metal) ou tipo 2 (sobre um sistema operacional).

**Características principais:**
- Kernel independente do host
- Total isolamento entre as VMs e o host
- Suporte a múltiplos sistemas operacionais (Linux, Windows, BSD etc.)
- Uso maior de recursos (RAM, CPU, armazenamento)
- Alta segurança e confiabilidade
- Ideal para virtualização de servidores, laboratórios complexos, testes com sistemas operacionais distintos

---

### 📦 Contêineres LXC

LXC (Linux Containers) é uma tecnologia de conteinerização que permite criar ambientes isolados no mesmo kernel do sistema operacional host. Cada contêiner se comporta como um pequeno sistema Linux, mas não possui seu próprio kernel, utilizando o do host.

**Características principais:**
- Compartilham o kernel do host (apenas Linux)
- Leves e rápidos para iniciar
- Isolamento via namespaces e cgroups
- Excelente desempenho por rodar quase nativamente
- Ideal para múltiplas instâncias Linux, serviços em lote, ambientes de desenvolvimento, redes simuladas

---

### 🐳 Docker

Docker é uma plataforma de conteinerização voltada para o empacotamento, distribuição e execução de **aplicações** em ambientes isolados. Utiliza um modelo baseado em **imagens em camadas**, o que facilita a reprodutibilidade e o versionamento.

**Características principais:**
- Voltado para aplicação (não para sistemas completos)
- Extremamente leve e portátil
- Integra-se com orquestradores como Kubernetes e Docker Swarm
- Baseado em imagens, facilmente distribuíveis via Docker Hub
- Ideal para DevOps, microserviços, CI/CD, ambientes imutáveis

---

## 📊 Gráficos comparativos

### Uso de CPU
<img src="fig1.png" width="30%">

### Uso de RAM
<img src="fig2.png" width="30%">

### Tempo de Inicialização
<img src="fig3.png" width="30%">

### Isolamento
<img src="fig4.png" width="30%">

---

## 🔍 Comparativo Técnico

| Característica             | VMs                       | LXC                          | Docker                       |
|---------------------------|---------------------------|------------------------------|------------------------------|
| Kernel                    | Próprio                   | Compartilhado                | Compartilhado                |
| Inicialização             | Lenta (~20s)              | Rápida (~2s)                 | Instantânea (~1s)            |
| Uso de recursos           | Alto                      | Baixo                        | Muito baixo                  |
| Isolamento                | Forte                     | Médio                        | Leve a médio                 |
| Portabilidade             | Moderada                  | Alta                         | Muito alta                   |
| Compatibilidade           | Windows/Linux/BSD         | Linux                        | Linux/macOS/Windows (via Docker Engine) |
| Casos de uso              | Virtualização completa    | Sistemas Linux leves         | Microserviços, DevOps        |

---

## ✅ Resumo

- **VMs**: ideais para sistemas completos e múltiplos OS.
- **LXC**: leve, ideal para múltiplas instâncias Linux.
- **Docker**: melhor para aplicações portáveis e escaláveis.

---
