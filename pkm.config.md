---
id: pkm.config
title: Configuração Otimizada do Sistema PKM
desc: 'Configurações do Dendron e VS Code para máxima eficiência'
updated: 1750990616153
created: 1750990616153
---

# ⚙️ Configuração Otimizada do Sistema PKM

## Configurações do Dendron (dendron.yml)

```yaml
workspace:
  vaults:
    - fsPath: .
      name: pkm-main
  journal:
    dailyDomain: daily.journal
    name: journal
    dateFormat: y.MM.dd
    addBehavior: childOfDomain
    firstDayOfWeek: 1
  scratch:
    name: scratch
    dateFormat: y.MM.dd.HHmmss
    addBehavior: asOwnDomain
  graph:
    zoomSpeed: 1
    createStub: false
  lookupConfirmVaultOnCreate: true
  enableAutoCreateOnDefinition: true
  enableXVaultWikiLink: false
  workspaceVaultSyncMode: sync
  enableAutoFoldFrontmatter: true
  maxPreviewsCached: 10
  maxNoteLength: 204800
  enableUserTags: true
  enableHashTags: true
  enableLinkCandidates: true
  enablePrettifyPasteDatetime: true
```

## Configurações do VS Code (settings.json)

```json
{
  "dendron.defaultJournalName": "daily",
  "dendron.defaultJournalDateFormat": "y.MM.dd",
  "dendron.defaultJournalAddBehavior": "childOfDomain",
  "dendron.defaultScratchName": "capture",
  "dendron.defaultScratchDateFormat": "y.MM.dd.HHmmss",
  "dendron.enableAutoCreateOnDefinition": true,
  "dendron.enableLinkCandidates": true,
  "dendron.enableSmartRefs": true,
  "dendron.enableUserTags": true,
  "dendron.enableHashTags": true,
  "markdown.preview.breaks": true,
  "markdown.preview.linkify": true,
  "editor.wordWrap": "on",
  "editor.quickSuggestions": {
    "other": true,
    "comments": false,
    "strings": false
  },
  "files.autoSave": "afterDelay",
  "files.autoSaveDelay": 1000
}
```

## Atalhos Personalizados (keybindings.json)

```json
[
  {
    "key": "ctrl+shift+d",
    "command": "dendron.createDailyJournalNote",
    "when": "dendron:pluginActive"
  },
  {
    "key": "ctrl+shift+f",
    "command": "dendron.lookupNote",
    "args": {
      "noteType": "capture",
      "selectionType": "extract"
    },
    "when": "dendron:pluginActive"
  },
  {
    "key": "ctrl+shift+l",
    "command": "dendron.lookupNote",
    "args": {
      "noteType": "literature"
    },
    "when": "dendron:pluginActive"
  },
  {
    "key": "ctrl+shift+p",
    "command": "dendron.lookupNote",
    "args": {
      "noteType": "project"
    },
    "when": "dendron:pluginActive"
  },
  {
    "key": "ctrl+shift+g",
    "command": "dendron.showNoteGraph",
    "when": "dendron:pluginActive"
  },
  {
    "key": "ctrl+shift+r",
    "command": "dendron.refactorHierarchy",
    "when": "dendron:pluginActive"
  }
]
```

## Extensões Recomendadas

### Essenciais para PKM
- **Dendron** - Sistema principal de notas
- **Markdown All in One** - Edição avançada de Markdown
- **Markdown Preview Enhanced** - Preview melhorado
- **Git Graph** - Visualização do histórico
- **Todo Tree** - Gestão de tarefas

### Produtividade
- **Pomodoro Timer** - Técnica Pomodoro
- **Time Master** - Controle de tempo
- **Project Manager** - Gestão de projetos
- **Auto Rename Tag** - Renomeação automática

### Visualização
- **Graph** - Visualização de grafos
- **Mind Map** - Mapas mentais
- **Draw.io Integration** - Diagramas
- **PlantUML** - Diagramas técnicos

## Scripts de Manutenção

### Script de Backup Diário (PowerShell)

```powershell
# pkm-backup.ps1
$timestamp = Get-Date -Format "yyyy-MM-dd_HH-mm-ss"
$source = "C:\Users\70089478100\Dendron\notes"
$backup = "C:\Users\70089478100\Backups\PKM\pkm-backup-$timestamp"

Write-Host "Criando backup do PKM..."
Copy-Item -Path $source -Destination $backup -Recurse
Write-Host "Backup criado em: $backup"

# Manter apenas os últimos 7 backups
$backups = Get-ChildItem "C:\Users\70089478100\Backups\PKM" | Sort-Object CreationTime -Descending
if ($backups.Count -gt 7) {
    $backups[7..($backups.Count-1)] | Remove-Item -Recurse -Force
    Write-Host "Backups antigos removidos"
}
```

### Script de Limpeza Semanal (PowerShell)

```powershell
# pkm-weekly-cleanup.ps1
$notesPath = "C:\Users\70089478100\Dendron\notes"
$archivePath = "$notesPath\para.archives.auto"

Write-Host "Executando limpeza semanal..."

# Mover notas fleeting antigas para arquivo
$oldFleetingNotes = Get-ChildItem "$notesPath\zettel.fleeting.*" | Where-Object { $_.LastWriteTime -lt (Get-Date).AddDays(-7) }
foreach ($note in $oldFleetingNotes) {
    Move-Item $note.FullName "$archivePath\fleeting\$($note.Name)"
}

Write-Host "Limpeza concluída: $($oldFleetingNotes.Count) notas arquivadas"
```

## Configuração de Sincronização (Git)

### .gitignore Personalizado
```
# VS Code
.vscode/settings.json
.vscode/launch.json
.vscode/tasks.json

# Dendron
.dendron.cache.*
.dendron.port
.dendron.ws

# Arquivos temporários
*.tmp
*.temp
*~

# Logs
*.log

# Backups locais
backups/
```

### Hooks do Git

#### Pre-commit Hook
```bash
#!/bin/bash
# .git/hooks/pre-commit
echo "Verificando consistência do PKM..."

# Verificar links quebrados
dendron doctor --action=findBrokenLinks

# Validar schema
dendron doctor --action=validateSchema

echo "Verificação concluída!"
```

## Configuração de Produtividade

### Pomodoro Integrado
- **25 min**: Captura e processamento
- **5 min**: Revisão e conexões
- **25 min**: Criação de conteúdo
- **5 min**: Backup e organização

### Horários Otimizados
- **09:00-09:15**: Revisão da nota diária
- **12:00-12:15**: Processamento de capturas
- **17:00-17:30**: Revisão e arquivamento
- **Sexta 16:00-16:30**: Revisão semanal

## Monitoramento e Métricas

### KPIs do Sistema PKM
- Notas capturadas por dia
- Taxa de processamento (captura → permanente)
- Densidade de conexões no grafo
- Tempo médio de busca/recuperação
- Frequência de reutilização de conhecimento

### Dashboard Mental
```
📊 PKM Dashboard Semanal
├── 📝 Capturas: X notas
├── 🔄 Processadas: Y notas
├── 🎯 Permanentes: Z notas
├── 🔗 Conexões: W links
└── 💡 Reutilizações: V vezes
```

## Integração com Ferramentas Externas

### Aplicativos Mobile
- **Obsidian Mobile** - Sincronização com iCloud/Google Drive
- **Notion** - Captura rápida em movimento
- **Google Keep** - Notas de voz automáticas

### Ferramentas Web
- **Readwise** - Importação de highlights
- **Pocket** - Lista de leitura organizada
- **IFTTT/Zapier** - Automações entre apps

---

## Checklist de Configuração

- [ ] Configurar dendron.yml conforme especificado
- [ ] Ajustar settings.json do VS Code
- [ ] Configurar atalhos personalizados
- [ ] Instalar extensões recomendadas
- [ ] Configurar scripts de backup
- [ ] Configurar git e hooks
- [ ] Testar todos os workflows
- [ ] Configurar sincronização mobile
- [ ] Definir horários de manutenção
- [ ] Configurar métricas de acompanhamento

---

**Configuração completa**: Seu sistema PKM está otimizado para máxima eficiência!
**Próximos passos**: [[pkm.quick-start]] para começar a usar imediatamente.
