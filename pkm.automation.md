---
id: pkm.automation
title: Automação e Configuração do Sistema PKM
desc: 'Scripts e automações para o segundo cérebro'
updated: 1750990616153
created: 1750990616153
---

# Automação do Sistema PKM

Este documento descreve as automações implementadas para maximizar a eficiência do sistema PKM integrado.

## Configurações Implementadas

### 1. Schema Avançado

O sistema utiliza um schema hierárquico que automaticamente:
- Sugere templates apropriados para cada tipo de nota
- Organiza automaticamente a estrutura de pastas
- Facilita a navegação e busca

### 2. Templates Inteligentes

Cada tipo de nota possui um template específico:
- **Fleeting Notes**: Para captura rápida de ideias
- **Literature Notes**: Para processamento de leituras
- **Permanent Notes**: Para conhecimento destilado
- **Structure Notes**: Para mapas conceituais
- **PARA Projects**: Para gestão de projetos

### 3. Fluxo de Trabalho Automatizado

#### Processamento Diário (15 min)
```bash
# Script para revisar notas do dia
1. Abrir Dendron
2. Ctrl+Shift+D (nota diária)
3. Revisar pkm.code.capture.*
4. Mover para PARA appropriado
5. Processar em zettel.permanent se necessário
```

#### Processamento Semanal (30 min)
```bash
# Script para limpeza e organização
1. Revisar todas as fleeting notes
2. Converter relevantes em permanent
3. Atualizar structure notes
4. Revisar projetos PARA
5. Arquivar projetos concluídos
```

#### Processamento Mensal (60 min)
```bash
# Script para revisão profunda
1. Análise de padrões de conhecimento
2. Criação de novas structure notes
3. Revisão e atualização de áreas PARA
4. Limpeza de arquivos antigos
5. Backup do sistema
```

## Atalhos de Teclado Configurados

| Ação | Atalho | Descrição |
|------|--------|-----------|
| Nova nota diária | `Ctrl+Shift+D` | Cria/abre nota do dia atual |
| Busca rápida | `Ctrl+L` | Lookup de notas |
| Refatorar nota | `Ctrl+Shift+R` | Renomear mantendo links |
| Vista de grafo | `Ctrl+Shift+G` | Visualizar conexões |
| Nova nota fleeting | `Ctrl+Shift+F` | Template de ideia rápida |
| Nova nota literature | `Ctrl+Shift+T` | Template de leitura |

## Scripts de Automação

### Script de Sincronização Automática
```bash
#!/bin/bash
# pkm-sync.sh
echo "Sincronizando PKM..."
git add .
git commit -m "Auto-sync PKM - $(date)"
git push origin main
echo "PKM sincronizado com sucesso!"
```

### Script de Limpeza Semanal
```bash
#!/bin/bash
# pkm-cleanup.sh
echo "Executando limpeza semanal do PKM..."

# Mover fleeting notes antigas para arquivo
find . -name "*.fleeting.*" -mtime +7 -exec mv {} pkm.para.archives.fleeting/ \;

# Gerar relatório de notas órfãs
dendron doctor --action=findBrokenLinks

echo "Limpeza concluída!"
```

## Configuração do Dendron.yml

```yaml
workspace:
  vaults:
    - fsPath: .
      name: pkm-vault
  journal:
    dailyDomain: journal
    name: journal
    dateFormat: y.MM.dd
    addBehavior: childOfDomain
  scratch:
    name: scratch
    dateFormat: y.MM.dd.HHmmss
    addBehavior: asOwnDomain
  graph:
    zoomSpeed: 1
  lookupConfirmVaultOnCreate: true
  enableAutoCreateOnDefinition: true
  enableXVaultWikiLink: false
  workspaceVaultSyncMode: sync
  enableAutoFoldFrontmatter: false
  maxPreviewsCached: 10
  maxNoteLength: 204800
```

## Regras de Nomenclatura

### PARA
- `para.projects.[projeto].[subtarefa]`
- `para.areas.[area].[tópico]`
- `para.resources.[categoria].[recurso]`
- `para.archives.[tipo].[nome]`

### CODE
- `code.capture.[data].[ideia]`
- `code.organize.[projeto/area]`
- `code.distill.[tópico]`
- `code.express.[output]`

### Zettelkasten
- `zettel.fleeting.[timestamp].[tópico]`
- `zettel.literature.[autor].[obra]`
- `zettel.permanent.[id].[conceito]`
- `zettel.structure.[mapa].[tema]`

## Melhores Práticas de Automação

1. **Capture Everywhere**: Use mobile apps com sincronização para capturar ideias em qualquer lugar
2. **Process Regularly**: 15 min diários, 30 min semanais, 1h mensais
3. **Link Everything**: Sempre criar conexões entre conceitos relacionados
4. **Review and Refine**: Revisar notas antigas e melhorar conexões
5. **Express Frequently**: Usar o conhecimento em projetos e compartilhamentos

## Métricas de Sucesso

- Número de notas permanentes criadas por semana
- Densidade de conexões no grafo de conhecimento
- Tempo médio de captura para processamento
- Frequência de reutilização de conhecimento

---

## Links Importantes

- [[pkm.workflow]] - Fluxo de trabalho detalhado
- [[pkm.zettel]] - Sistema Zettelkasten
- [[pkm.para]] - Método PARA
- [[pkm.code]] - Método CODE
- [[templates.daily]] - Template de notas diárias
