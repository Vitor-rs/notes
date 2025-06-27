---
id: pkm.resources.para
title: Método PARA de Tiago Forte
desc: 'Explicação detalhada do método PARA'
updated: 1719593816153
created: 1719593816153
---

# Método PARA - Sistema de Organização Universal

O método PARA, criado por Tiago Forte, é um sistema para organizar qualquer tipo de informação digital em quatro categorias simples.

## O que significa PARA?

PARA é um acrônimo que representa as quatro categorias fundamentais de organização:

### P - Projects (Projetos)

**Definição:** Empreendimentos com objetivo definido e data de conclusão.

**Características:**
- Têm um resultado específico a ser alcançado
- Têm prazo definido (mesmo que seja flexível)
- Envolvem uma série de tarefas para completar
- São "concluíveis" - podem ser marcados como finalizados

**Exemplos:**
- Lançar um novo produto
- Planejar uma viagem
- Escrever um artigo
- Renovar a cozinha
- Completar um curso online

### A - Areas (Áreas)

**Definição:** Esferas de responsabilidade contínua sem data de conclusão.

**Características:**
- Não têm objetivo final nem data de conclusão
- Exigem manutenção contínua ao longo do tempo
- Têm padrões a serem mantidos indefinidamente
- São responsabilidades pessoais ou profissionais

**Exemplos:**
- Saúde
- Finanças
- Relacionamentos
- Desenvolvimento profissional
- Funções no trabalho (marketing, RH, etc.)

### R - Resources (Recursos)

**Definição:** Tópicos ou temas de interesse contínuo.

**Características:**
- São coleções de conhecimento sobre um tema
- Não exigem ação imediata
- Servem como referência para projetos futuros
- Representam áreas que você quer explorar ou aprender

**Exemplos:**
- Design gráfico
- História da arte
- Ciência de dados
- Receitas culinárias
- Técnicas de meditação

### A - Archives (Arquivos)

**Definição:** Itens inativos das outras três categorias.

**Características:**
- Projetos concluídos ou abandonados
- Áreas de responsabilidade que não são mais relevantes
- Recursos que não são mais de interesse
- Mantidos para referência histórica ou consulta ocasional

**Exemplos:**
- Projetos concluídos
- Documentação de produtos antigos
- Cursos finalizados
- Papéis de trabalhos anteriores

## Princípios Fundamentais do PARA

### 1. Organizar por Acionabilidade

O PARA organiza informações com base em quão acionáveis elas são, não em suas características intrínsecas.

A ordem das categorias reflete um espectro de acionabilidade:
1. **Projetos** - Altamente acionáveis, exigem atenção imediata
2. **Áreas** - Exigem manutenção regular
3. **Recursos** - Consultados conforme necessário
4. **Arquivos** - Raramente consultados

### 2. Separar Projetos de Áreas

Um erro comum é confundir projetos com áreas. Isso leva à sensação de nunca terminar nada.

**Áreas geram projetos:**
- Área: Saúde → Projeto: Correr uma maratona
- Área: Finanças → Projeto: Criar orçamento mensal
- Área: Desenvolvimento profissional → Projeto: Obter certificação

### 3. Rotação Constante

O sistema é dinâmico, não estático:

- Projetos são concluídos e movidos para Arquivos
- Novos projetos são criados a partir de Áreas ou Recursos
- Recursos podem se transformar em Projetos quando decidimos agir
- Áreas podem ser desativadas e movidas para Arquivos

### 4. Número Limitado de Categorias

Independentemente do volume de informações, são apenas quatro categorias.

A simplicidade do sistema permite:
- Rápida tomada de decisões sobre onde arquivar
- Fácil recuperação de informações
- Manutenção sustentável a longo prazo

## Implementação do PARA no Dendron

A estrutura hierárquica do Dendron é perfeita para implementar o PARA:

```
pkm.para.projects
pkm.para.areas
pkm.para.resources
pkm.para.archives
```

Cada categoria pode ter hierarquias adicionais:

```
pkm.para.projects.trabalho.projeto-x
pkm.para.projects.pessoal.renovacao-casa
pkm.para.areas.saude.exercicios
pkm.para.resources.programacao.python
```

## Processo de Revisão

Para manter o PARA funcionando eficientemente:

1. **Revisão Semanal:**
   - Atualizar status de projetos
   - Verificar se novos projetos precisam ser criados
   - Mover projetos concluídos para Arquivos

2. **Revisão Mensal:**
   - Avaliar áreas de responsabilidade
   - Verificar equilíbrio entre as áreas
   - Atualizar recursos com novos materiais

3. **Revisão Trimestral:**
   - Auditar todo o sistema
   - Arquivar recursos não mais relevantes
   - Avaliar alinhamento entre projetos e objetivos maiores

## Benefícios do PARA

1. **Clareza Mental:** Saber exatamente onde colocar e encontrar informações
2. **Foco em Projetos:** Visibilidade clara sobre o que precisa ser concluído
3. **Simplicidade:** Sistema fácil de aprender e manter
4. **Flexibilidade:** Funciona com qualquer ferramenta ou aplicativo
5. **Escalabilidade:** Eficaz para pequenas ou grandes coleções de informação

## Recursos Adicionais

- [Artigo original sobre PARA (Tiago Forte)](https://fortelabs.com/blog/para/)
- [Building a Second Brain (Livro)](https://www.buildingasecondbrain.com/)
