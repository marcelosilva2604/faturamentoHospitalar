# 🏥 Sistema de Faturamento Hospitalar - SUS

[![GitHub](https://img.shields.io/badge/GitHub-faturamentoHospitalar-blue?logo=github)](https://github.com/marcelosilva2604/faturamentoHospitalar)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Data Source](https://img.shields.io/badge/Data%20Source-DATASUS-red)](http://datasus.saude.gov.br/)

Este repositório contém **tabelas oficiais do Sistema Único de Saúde (SUS)** para desenvolvimento de sistemas de faturamento hospitalar, codificação médica e análise de dados em saúde.

## 📁 Estrutura do Projeto

```
📦 faturamento-sus/
├── 📋 cid10/                    # Classificação Internacional de Doenças
│   ├── CID-10-CAPITULOS.CSV    # 22 capítulos principais
│   ├── CID-10-GRUPOS.CSV       # Grupos de doenças (261 grupos)
│   ├── CID-10-CATEGORIAS.CSV   # Categorias específicas (2,037 categorias)
│   └── CID-10-SUBCATEGORIAS.CSV # Códigos detalhados (14,190+ códigos)
├── 💰 sigtap/                   # Sistema de Gerenciamento da Tabela de Procedimentos
│   └── README.md               # Instruções para download oficial
└── 📖 README.md                # Este arquivo
```

## 🩺 Tabelas CID-10 - Classificação Internacional de Doenças

### 📊 Estatísticas das Tabelas
| Arquivo | Descrição | Registros Aprox. | Uso Principal |
|---------|-----------|------------------|---------------|
| **CAPITULOS** | Agrupamentos principais (A-Z) | 22 | Navegação geral |
| **GRUPOS** | Subdivisões por capítulo | 261 | Classificação intermediária |
| **CATEGORIAS** | Códigos de 3 dígitos | 2,037 | Codificação básica |
| **SUBCATEGORIAS** | Códigos de 4+ dígitos | 14,190+ | Codificação específica |

### 🔍 Exemplos de Códigos CID-10 Frequentes em Pediatria
```csv
Código   | Descrição                                    | Categoria
---------|----------------------------------------------|------------
J21      | Bronquiolite aguda                          | Respiratória
J18      | Pneumonia por agente não especificado      | Respiratória  
A09      | Diarreia e gastroenterite infecciosa       | Gastrointestinal
P28      | Afecções respiratórias período perinatal   | Perinatal
Z38      | Nascidos vivos segundo local nascimento    | Administrativa
```

## 💰 SIGTAP - Tabela de Procedimentos e Valores

### 📋 O que é o SIGTAP?
O **Sistema de Gerenciamento da Tabela de Procedimentos, Medicamentos e OPM do SUS** define:

- ✅ **Valores de remuneração** para todos os procedimentos SUS
- ✅ **Códigos de procedimentos** médicos e hospitalares  
- ✅ **Estrutura de custos** AIH (Autorização de Internação Hospitalar)
- ✅ **Especialidades médicas** e modalidades de atendimento

### 💡 Componentes da Remuneração AIH
```
🏥 Serviços Hospitalares     ➜ Custos básicos da internação
👨‍⚕️ Serviços Profissionais    ➜ Honorários médicos
🔬 SADT                      ➜ Exames e diagnósticos
👶 Recém-nascidos           ➜ Cuidados neonatais específicos
👨‍👩‍👧‍👦 Acompanhante           ➜ Hospedagem (direito em pediatria)
🦴 Órteses/Próteses         ➜ Dispositivos médicos
🩸 Hemoterapia              ➜ Transfusões e derivados
```

### 📥 Como Baixar Dados SIGTAP Atualizados
```bash
# 1. Acesse o site oficial
https://sigtap.datasus.gov.br/tabela-unificada/app/download.jsp

# 2. Selecione a competência (mês/ano)
# 3. Baixe o arquivo ZIP
# 4. Extraia os arquivos TXT nesta pasta
```

## 🚀 Casos de Uso

### 🏥 Desenvolvimento de Sistemas
```python
# Exemplo: Buscar código CID-10
import pandas as pd

# Carregar tabela de subcategorias
cid10 = pd.read_csv('cid10/CID-10-SUBCATEGORIAS.CSV')

# Buscar pneumonia
pneumonias = cid10[cid10['DESCRICAO'].str.contains('pneumonia', case=False)]
print(pneumonias[['CODIGO', 'DESCRICAO']].head())
```

### 📊 Análise de Dados
- **Epidemiologia hospitalar** - Análise de frequência de diagnósticos
- **Gestão de custos** - Otimização de valores de procedimentos
- **Auditoria médica** - Validação de códigos e valores
- **Business Intelligence** - Dashboards e relatórios gerenciais

### 🔧 Integração com Sistemas
- **EMR/EHR** - Prontuários eletrônicos
- **HIS** - Sistemas de informação hospitalar  
- **Sistemas de faturamento** - TISS, CBHPM
- **APIs do SUS** - CNESNet, SIASUS, SIHD

## 📊 Dados Epidemiológicos de Referência

### 👶 Pediatria - Principais Causas de Internação
| Período | Categoria | % Internações | Observação |
|---------|-----------|---------------|------------|
| 2018-2019 | Doenças Respiratórias | 23.52% | Principal causa |
| 2018-2019 | Afecções Perinatais | 17.04% | Segunda maior |
| 2020-2021 | Afecções Perinatais | 22.64% | ↗️ Aumento pandemia |
| 2020-2021 | Causas Externas | 14.59% | Acidentes/violências |

### 🌍 Dados Regionais (Exemplo: Gastroenterite Nordeste 2019-2023)
- **Total de casos**: 84.045
- **Custo total**: R$ 32.262.847,03  
- **Maior incidência**: Maranhão (31.146 casos)
- **Perfil**: 52,69% sexo masculino, 50,58% na faixa 1-4 anos

## 🔄 Atualizações e Manutenção

### 📅 Frequência de Atualização
- **CID-10**: Estável (última revisão: CID-11 em desenvolvimento)
- **SIGTAP**: **Mensal** (nova competência todo mês)

### 🔄 Como Atualizar este Repositório
```bash
# 1. CID-10 (automático via script)
wget https://raw.githubusercontent.com/cleytonferrari/CidDataSus/master/...

# 2. SIGTAP (manual)
# Baixe do site oficial e substitua os arquivos em sigtap/
```

## 📖 Fontes e Referências Oficiais

### 🏛️ Órgãos Responsáveis
- **Ministério da Saúde** - Definição de políticas
- **DATASUS** - Gestão de dados e sistemas
- **ANS** - Regulação de planos de saúde (TISS)

### 🌐 Links Oficiais
| Recurso | URL | Descrição |
|---------|-----|-----------|
| **SIGTAP** | http://sigtap.datasus.gov.br/ | Tabela oficial de procedimentos |
| **DATASUS** | https://datasus.saude.gov.br/ | Portal de dados SUS |
| **CID-10** | https://icd.who.int/browse10/2019/en | OMS - Classificação oficial |
| **FTP DATASUS** | ftp://ftp2.datasus.gov.br/pub/sistemas/tup/downloads/ | Downloads diretos |

## 🤝 Contribuição

### 📝 Como Contribuir
1. **Fork** este repositório
2. **Crie** uma branch para sua feature (`git checkout -b feature/nova-funcionalidade`)
3. **Commit** suas mudanças (`git commit -am 'Adicionar nova funcionalidade'`)
4. **Push** para a branch (`git push origin feature/nova-funcionalidade`)
5. **Abra** um Pull Request

### 🐛 Reportar Problemas
- Use as [Issues](https://github.com/marcelosilva2604/faturamentoHospitalar/issues) para reportar bugs
- Inclua informações sobre versão dos dados e contexto do problema

## 📄 Licença

Este projeto está licenciado sob a licença MIT - veja o arquivo [LICENSE](LICENSE) para detalhes.

**Nota**: Os dados SUS são de domínio público conforme determinação do Ministério da Saúde.

## ⚖️ Disclaimer Legal

⚠️ **IMPORTANTE**: Este repositório contém dados oficiais para fins educacionais e de desenvolvimento. Para uso em produção:

- ✅ **Sempre utilize** as tabelas mais recentes do DATASUS
- ✅ **Valide** a competência dos dados SIGTAP  
- ✅ **Consulte** a legislação vigente sobre faturamento SUS
- ✅ **Implemente** controles de qualidade e auditoria

---

<div align="center">

**🏥 Desenvolvido para facilitar a criação de sistemas de saúde no Brasil 🇧🇷**

[⭐ Star este repo](https://github.com/marcelosilva2604/faturamentoHospitalar) | [🐛 Reportar Bug](https://github.com/marcelosilva2604/faturamentoHospitalar/issues) | [💡 Solicitar Feature](https://github.com/marcelosilva2604/faturamentoHospitalar/issues)

</div>