# Exemplos e Referências

Esta pasta contém exemplos e referências de implementação para cada etapa do desafio, usando o projeto **San (multiagente)** como base: **Streamlit + Ollama + LangGraph + dados mock (CSV/JSON)**.

## Vídeos de Referência

> 🎬 Sugestão: grave vídeos curtos (2–5 min) por etapa mostrando o “antes/depois” e a decisão técnica. Isso ajuda muito na avaliação e na apresentação final.

| Etapa                | Descrição                                                            | 
| -------------------- | -------------------------------------------------------------------- | 
| Documentação         | Caso de uso, personas (3 modos) e arquitetura com LangGraph          | 
| Base de Conhecimento | Como o agente lê CSV/JSON, reduz contexto e filtra por agente        | 
| Prompts              | System prompts (Guardião/Finanças/Autopiloto), edge cases e exemplos | 
| Aplicação            | Streamlit chat + Ollama + roteamento + checker                       | 
| Métricas             | Roteamento correto, segurança, consistência e latência               | 
| Pitch                | Roteiro e demo prática do agente                                     | 

---

## Referências Internas do Repositório

Use estes arquivos para navegar pelo projeto:

* **Aplicação (Streamlit + LangGraph + Ollama):** `src/app.py`
* **Documentação do agente:** `docs/01-documentacao-agente.md`
* **Base de conhecimento (CSV/JSON):** `docs/02-base-conhecimento.md`
* **Prompts e exemplos de interação:** `docs/03-prompts.md`
* **Avaliação e métricas:** `docs/04-metricas.md`
* **Pitch (roteiro 3 min):** `docs/05-pitch.md`

---

## Exemplo de Implementação Simples

A implementação principal está em `src/app.py` e inclui:

* **3 agentes/personas** (Guardião, Finanças, Autopiloto)
* **Roteamento de intenção** (Guardião com prioridade)
* **Contexto com dados mock** (`perfil_investidor.json`, `transacoes.csv`, `historico_atendimento.csv`, `produtos_financeiros.json`)
* **Redução de contexto** (tail + resumo de produtos) para melhorar performance
* **Orquestração LangGraph** (`router → build_prompt → llm → checker`)
* **Integração com Ollama** via `/api/generate`

### Prompt rápido para testar (copiar e colar)

* Golpe:

  * “Recebi WhatsApp pedindo taxa de liberação do Pix. É verdade?”
* Educação:

  * “Explica CDI e SELIC de um jeito simples.”
* Planejamento:

  * “Como eu faço um plano pra sobrar dinheiro todo mês com base nas minhas transações?”

---

## Pequenos “Exemplos” (ideias de arquivos extras aqui em `examples/`)

Se quiser deixar esta pasta ainda mais útil, você pode adicionar:

* `examples/prompts_testes.md` → lista de prompts por agente (Guardião/Finanças/Autopiloto)
* `examples/checklist_validacao.md` → checklist rápido de segurança (não pedir dados sensíveis, 3 parágrafos, etc.)
* `examples/script_testes.py` → script simples medindo latência e verificando regras

