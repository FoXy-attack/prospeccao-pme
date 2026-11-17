# Instalação

## Pré-requisitos

- Conta Google com Google Sheets
- Conta no Claude com Cowork e rotinas agendadas
- Conta no Zapier com o conector MCP ligado ao Claude
- Robô de envio em Google Apps Script (seu próprio script, não incluído aqui)

## Passo a passo

1. **Crie a planilha** "CRM Prospecção" com as abas `Leads` e `Config`, seguindo [planilha.md](planilha.md). Você pode importar [exemplos/leads-exemplo.csv](../exemplos/leads-exemplo.csv) para ver o formato.
2. **Instale o robô** de envio no Apps Script da planilha (Extensões → Apps Script) e crie um gatilho de tempo. Comece com **Modo teste = SIM** na aba Config.
3. **Conecte o Google Sheets no Zapier** e habilite as ações *Get Data Range* e *Create Multiple Spreadsheet Rows*.
4. **Preencha as variáveis** de [config/variaveis.example.env](../config/variaveis.example.env): ID da planilha, ID das abas (número depois de `gid=` na URL) e o `connection_id` do Zapier.
5. **Crie as duas rotinas agendadas** no Claude com os prompts de [prompts/](../prompts/), trocando os `{{...}}` pelos seus valores e usando os horários de [config/agendamentos.json](../config/agendamentos.json).
6. **Teste**: rode a captação manualmente, confira as linhas na planilha e veja o robô enviar para o e-mail de teste.
7. **Ligue de verdade**: Modo teste = NÃO, limite diário = 5. Siga o checklist de [entregabilidade.md](entregabilidade.md) antes de subir o volume.
