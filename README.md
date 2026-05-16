# SendPulse - Campanha via Telegram com n8n

Workflow n8n para criação, análise e enfileiramento de campanhas de e-mail marketing no SendPulse usando comandos via Telegram.

Este fluxo permite:

- Gerar sugestões de campanhas com IA com base nas últimas campanhas do SendPulse.
- Receber campanhas aprovadas pelo Telegram em formato JSON.
- Salvar campanhas aprovadas em uma fila interna do n8n.
- Processar a fila automaticamente em intervalos definidos.
- Criar campanhas no SendPulse com HTML convertido para Base64.
- Adicionar `utm_campaign` automaticamente nos links do HTML.
- Inserir `preheader` oculto no corpo do e-mail.
- Confirmar pelo Telegram quando uma campanha entra na fila ou é criada.

---

## Visão geral do fluxo

O workflow possui três rotas principais acionadas pelo mesmo bot do Telegram:

### 1. Comando `/campanha`

Retorna um modelo JSON para criação de campanha.

Exemplo de retorno:

```json
{
  "nome_remetente": "xxxxxxx xxxxxx",
  "email_remetente": "xxxxx@xxxxxx.com.br",
  "nome_campanha": "Campanha Kit Bebidas Maio 2026",
  "assunto": "🥂 Brinde Com Estilo Usando Nosso Kit Bebida Personalizado",
  "preheader": "Identidade • Embalagem • Design",
  "data_envio": "2026-05-16 07:33:00",
  "url_html": "https://xxxxxx.com.br/news/xxxx",
  "utm_campaign": "kit_bebidas_personalizados_maio_2026"
}
