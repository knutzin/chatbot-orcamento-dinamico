# Chatbot com Controle de Orçamento Dinâmico

Projeto 16 — Miniagente com IA LLM, disciplina de Inteligência Artificial, PUC-SP.

## Integrantes

- **Pedro Isamu Yoshissaro** — [Knutzin](https://github.com/Knutzin)
- **Nicolas mariano da silva** — [nickmds1](https://github.com/nickmds1)

## Executar

[Abrir notebook no Google Colab](https://colab.research.google.com/github/knutzin/chatbot-orcamento-dinamico/blob/main/Chatbot_Orcamento_Dinamico.ipynb)

1. Abra o notebook no Colab.
2. Cadastre `OPENAI_API_KEY` no painel **Secrets** e permita acesso ao notebook.
3. Execute as células em ordem e converse pela interface.

As chamadas exigem chave e créditos da API da OpenAI. O orçamento padrão é de **US$ 0,02 por instância**.
Reexecutar a célula que cria o chat reinicia a contabilidade local, mas não a cobrança na conta.

## Funcionalidades

- Estimativa local dos tokens do contexto enquanto o usuário digita.
- Contagem remota de entrada antes da geração.
- Custo por chamada e acumulado, calculado com `Decimal` e `usage` da API.
- Resumo automático quando o contexto ultrapassa 1.000 tokens.
- Inclusão do custo dos resumos no orçamento.
- Reserva conservadora de saldo antes de cada geração.
- Tabela de auditoria e gráfico do custo acumulado.

## Tecnologias

Python, OpenAI SDK (Responses API), GPT-5 nano, tiktoken, ipywidgets, pandas e matplotlib.
As dependências são instaladas na primeira célula do notebook.

## Validação e limitações

O notebook também inclui um **cenário ilustrativo com dados fictícios**, contendo conversa,
tabela de tokens, custos por chamada, resumo e conclusão. O total calculado nesse cenário
é de US$ 0,00040700. Ele pode ser lido sem executar o código e não representa medições da API.

A sintaxe e a lógica foram verificadas localmente com uma API simulada, incluindo cálculo com cache,
bloqueio por saldo insuficiente, compactação, mensagem longa e preservação do histórico após falhas.
O notebook inclui oito verificações automatizadas reproduzíveis e os resultados da execução local
com API simulada. No exemplo, a contagem artificial caiu de 1.220 para 669; isso não é
uma medição de tokens do modelo real. A validação de qualidade dos resumos, custos reais e
interface no Colab permanece pendente.

A contagem local é uma estimativa. O custo final usa o consumo informado pela API e as tarifas
configuradas; não inclui impostos, créditos ou futuras mudanças de preço. Resumos podem perder
informações, por isso o notebook inclui um roteiro para avaliar a preservação de fatos.

## Referências

- [Notebook da aula](https://colab.research.google.com/drive/1jMFJcwWZW_OdkP0VUtXqfnQ_4G59yaK_)
- [GPT-5 nano e preços](https://developers.openai.com/api/docs/models/gpt-5-nano)
- [Contagem de tokens](https://developers.openai.com/api/docs/guides/token-counting)