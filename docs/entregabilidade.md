# Entregabilidade e LGPD: checklist

Prospecção por e-mail só funciona se os e-mails chegarem à caixa de entrada. Este checklist cobre os quatro pontos que mais derrubam remetentes novos.

## 1. Autenticação do domínio (SPF, DKIM, DMARC)

| Situação | O que fazer |
|---|---|
| Envio por conta **@gmail.com** | SPF, DKIM e DMARC são do domínio do Google, e o Google já os mantém. Não há o que configurar (nem é possível). O limite real é a reputação da conta, então o ritmo baixo é a proteção principal. |
| Envio por **domínio próprio** (ex.: Google Workspace) | Configurar no DNS: **SPF** (`v=spf1 include:_spf.google.com ~all`), **DKIM** (gerar a chave no Admin do Workspace e publicar o TXT), **DMARC** (começar com `v=DMARC1; p=none; rua=mailto:dmarc@seudominio.com.br` e endurecer depois). Testar em mail-tester.com antes de ativar o robô. |

Recomendação para escalar: migrar para domínio próprio, de preferência um subdomínio ou domínio secundário só para prospecção, para não arriscar o domínio principal.

## 2. Aquecimento (warm-up)

O sistema já nasce conservador:

- Robô limitado a **5 envios/dia** na aba Config
- Captação só repõe a fila quando ela tem menos de 5 empresas

Sugestão de rampa, subindo só se não houver bounces nem marcações de spam:

| Semana | Limite diário |
|---|---|
| 1–2 | 5 |
| 3 | 10 |
| 4 | 15 |
| 5+ | 20–30 |

Ao subir o limite na aba Config, ajuste também o número "5" no prompt de captação.

## 3. Qualidade dos e-mails (evitar hard bounce)

Já aplicado na captação:

- Só entra e-mail que foi **visto publicado** (site oficial ou diretório), nunca deduzido
- Só domínio próprio da empresa; provedores genéricos e contabilidades são descartados
- Preferência por caixas monitoradas (rh@, comercial@, contato@) em vez de SAC ou recrutamento
- Fonte registrada na coluna L de cada lead

Melhorias possíveis:

- Checar se o domínio tem registro **MX** antes de gravar o lead
- Pausar a captação automaticamente se a taxa de `E-mail inválido` passar de 3%

## 4. LGPD e opt-out

E-mail B2B para endereços corporativos genéricos (contato@, comercial@) tem base no **legítimo interesse** (art. 7º, IX, LGPD), desde que haja transparência e opção clara de saída. Todo e-mail do robô deve ter:

- Identificação de quem envia (nome, função, empresa/corretora, telefone)
- Motivo do contato em uma frase
- **Rodapé de descadastro**, por exemplo:

  > Se não quiser mais receber mensagens minhas, responda este e-mail com "REMOVER" e retiro seu contato da lista no mesmo dia.

- Respeitar o pedido: status `Descadastrou` na planilha, e nunca mais enviar para aquele e-mail (a captação já bloqueia duplicados, inclusive descadastrados)

> Isto é uma orientação geral, não parecer jurídico. Em caso de dúvida, consulte um advogado especializado em proteção de dados.
