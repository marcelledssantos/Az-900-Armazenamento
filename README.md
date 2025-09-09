# Resumo sobre Armazenamento no Microsoft Azure

## Entendendo o Desafio
Este repositório faz parte do desafio proposto na DIO, com o objetivo de documentar o aprendizado sobre os serviços de **armazenamento do Azure**.  
A proposta é explorar os conceitos apresentados no laboratório, registrar os pontos principais e consolidar os conhecimentos adquiridos para uso em futuras implementações e como material de estudo para a certificação **AZ-900 (Azure Fundamentals)**.

---

## Serviços de Armazenamento no Azure

O **Azure Storage** é a solução de armazenamento em nuvem da Microsoft que permite guardar e acessar dados de forma segura, escalável e altamente disponível. Ele oferece diferentes serviços de acordo com a necessidade:

- **Blob Storage**  
  Armazena **dados não estruturados** como imagens, vídeos, backups e documentos.  
  - Tipos de blobs: *Block Blob* (arquivos comuns), *Append Blob* (logs) e *Page Blob* (discos virtuais VHD).  
  - Ideal para cenários de dados grandes e acesso via URL.

- **Azure Files**  
  Compartilhamento de arquivos em nuvem usando protocolos conhecidos como **SMB** e **NFS**.  
  - Permite substituir servidores de arquivos locais.  
  - Pode ser montado em múltiplas VMs.

- **Disk Storage**  
  Discos persistentes para máquinas virtuais no Azure.  
  - Tipos: SSD Standard, SSD Premium, Ultra Disk e HDD.  
  - Usados para sistemas operacionais, dados e aplicações.

- **Queue Storage**  
  Sistema de mensagens assíncronas para comunicação entre componentes.  
  - Facilita arquiteturas desacopladas e processamento em segundo plano.

- **Table Storage**  
  Banco de dados NoSQL simples e econômico.  
  - Estrutura de chave/valor.  
  - Alternativa leve ao Azure Cosmos DB.

---

## Camadas de Acesso (Access Tiers)

O Azure permite otimizar custos com diferentes níveis de acesso:

- **Hot** → Dados acessados frequentemente.  
- **Cool** → Dados pouco acessados (mínimo de 30 dias de retenção).  
- **Archive** → Dados raramente acessados e armazenados a longo prazo (mínimo de 180 dias de retenção).  

Exemplo: Relatórios anuais podem ser armazenados na camada **Archive**, enquanto arquivos usados no dia a dia ficam em **Hot**.

---

## Redundância e Alta Disponibilidade

Para garantir segurança contra falhas e perda de dados, o Azure oferece diferentes modelos de replicação:

| Tipo | Cópias | Região | Protege contra | Durabilidade | SLA Disponibilidade |
|------|--------|--------|----------------|--------------|----------------------|
| **LRS** (Locally Redundant Storage) | 3 | 1 datacenter | Falha de hardware local | 11 noves (99,999999999%) | 99,9% |
| **ZRS** (Zone-Redundant Storage) | 3 | Zonas de uma região | Falha de zona inteira | 11 noves | 99,9% |
| **GRS** (Geo-Redundant Storage) | 6 | 2 regiões | Falha regional (com failover) | 11 noves | 99,9% |
| **RA-GRS** (Read-Access GRS) | 6 | 2 regiões | Falha regional + leitura na secundária | 11 noves | 99,99% leitura |
| **GZRS** (Geo-Zone Redundant Storage) | 6 | Zonas + outra região | Falha de zona + falha regional | 11 noves | 99,9% (99,99% com RA) |

### Importante:
- Os **11 noves (99,999999999%)** se referem à **durabilidade dos objetos** – ou seja, a chance de perda de dados é praticamente nula.  
- O **SLA de disponibilidade** está ligado à capacidade de acessar os dados, variando entre **99,9% e 99,99%** dependendo da redundância escolhida.

---

## Segurança e Acesso

O Azure Storage oferece mecanismos para manter os dados protegidos:

- **Chaves de acesso**: cada conta de armazenamento possui duas chaves para autenticação.  
- **SAS (Shared Access Signature)**: links temporários com permissões restritas.  
- **RBAC (Role-Based Access Control)**: controle de acesso baseado em funções.  
- **Criptografia automática**: todos os dados são criptografados em repouso (AES-256).  

---

## Ferramentas de Gerenciamento

Existem diferentes formas de interagir com os dados armazenados:

- **Portal do Azure** → interface gráfica via navegador.  
- **Azure Storage Explorer** → ferramenta gráfica dedicada.  
- **Azure CLI / PowerShell** → gerenciamento via linha de comando.  
- **SDKs e APIs REST** → integração em aplicações.  

---

## Conclusão

Durante este laboratório, aprendi que o **armazenamento no Azure** é flexível e cobre diferentes cenários, desde simples arquivos até arquiteturas distribuídas globais.  
Os principais pontos de atenção para certificação **AZ-900** são:  
- Saber identificar qual serviço usar em cada cenário.  
- Entender as camadas de acesso (Hot, Cool e Archive).  
- Conhecer os tipos de redundância (LRS, ZRS, GRS, RA-GRS, GZRS).  
- Saber diferenciar **durabilidade (11 noves)** de **SLA de disponibilidade**.  

Esse conhecimento é essencial para compreender como o Azure garante **segurança, disponibilidade e escalabilidade** no armazenamento em nuvem.

---
