# Sistema de Faturamento Hospitalar - SUS

Este repositório contém tabelas oficiais do Sistema Único de Saúde (SUS) para desenvolvimento de sistemas de faturamento hospitalar.

## Conteúdo

### 📋 CID-10 - Classificação Internacional de Doenças
- **cid10/CID-10-CAPITULOS.CSV** - Capítulos da CID-10
- **cid10/CID-10-GRUPOS.CSV** - Grupos de doenças
- **cid10/CID-10-CATEGORIAS.CSV** - Categorias específicas
- **cid10/CID-10-SUBCATEGORIAS.CSV** - Subcategorias detalhadas

### 💰 SIGTAP - Sistema de Gerenciamento da Tabela de Procedimentos
- **sigtap/README.md** - Instruções para download da tabela oficial
- Contém valores de remuneração dos procedimentos SUS
- Estrutura de custos AIH (Autorização de Internação Hospitalar)

## Fonte dos Dados
- **CID-10**: Repositório oficial DATASUS via GitHub
- **SIGTAP**: http://sigtap.datasus.gov.br/ (download manual necessário)

## Uso
Estas tabelas servem como base para:
- Sistemas de faturamento hospitalar
- Codificação médica
- Análise de custos hospitalares
- Integração com sistemas do SUS

## Atualização
- **CID-10**: Dados atualizados automaticamente do repositório oficial
- **SIGTAP**: Requer download manual da competência desejada