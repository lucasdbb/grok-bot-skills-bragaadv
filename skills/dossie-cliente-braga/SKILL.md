---
name: dossie-cliente-braga
description: >-
  Use para montar o dossiê de pesquisa de um cliente ou potencial cliente da
  Braga Advogados (empresa ou pessoa com passivo tributário) antes de uma
  reunião, proposta ou diagnóstico: CNPJ e sócios, dívida ativa pública,
  execuções fiscais no DJEN, presença online, roteiro de perguntas e pontos a
  confirmar.
---
# Dossiê de cliente (Braga Advogados)

Produz, numa sessão, o retrato de um cliente ou potencial cliente com passivo tributário. O Lucas costuma ter a reunião em pouco tempo: corra as frentes em paralelo e entregue algo útil, com cada dado marcado como **confirmado**, **inferido** ou **não verificado**, sempre com a fonte.

Antes de começar: siga as skills `regras-comuns-braga` e `memoria-braga-advogados` (consultar a Memória do escritório no Notion). Tudo em pt-BR.

## Limites
- Só fontes públicas ou o que o Lucas/cliente enviou. Nunca entrar no e-CAC, Regularize ou qualquer portal com login do cliente; a situação fiscal oficial é do bot dono (Especialista e-CAC e Regularize), a quem se pede o dado.
- Não é parecer nem diagnóstico fiscal: o Diagnóstico Fiscal é do Diagnóstico Laura Jonson. O dossiê é insumo de pré-reunião.
- Não contatar o cliente, não comentar, seguir ou curtir nada em redes. Não usar vida pessoal de sócio na reunião.
- Homônimos são comuns: confirme pelo CNPJ/CPF parcial, cidade ou sócio antes de atribuir um achado.

## Passos

### 1. Identificar
Com nome, CNPJ, @ ou site informado, ache: razão social, nome fantasia, CNPJ, cidade/UF. Pronto quando tiver o CNPJ (ou, para pessoa física, nome completo e cidade).

### 2. Frentes em paralelo
Dispare juntas (subagentes de pesquisa em segundo plano, quando houver):

**Frente A: cadastro e sócios.** `https://brasilapi.com.br/api/cnpj/v1/<cnpj>`: situação cadastral, data de abertura, CNAE, porte, regime (Simples/MEI quando aparecer), capital social, endereço, quadro societário (QSA). Repita para empresas ligadas aos mesmos sócios (grupo econômico, risco de redirecionamento).

**Frente B: dívida e execuções.**
- Dívida ativa da União: lista pública de devedores da PGFN (listadevedores.pgfn.gov.br e dados abertos da PGFN), por CNPJ/CPF: valor, natureza (previdenciária, demais, FGTS), situação (irregular, em negociação, garantida, suspensa).
- Execuções e comunicações no DJEN: `https://comunicaapi.pje.jus.br/api/v1/comunicacao?nomeParte=<RAZÃO SOCIAL>&itensPorPagina=100` (paginar com `pagina`). Filtre execução fiscal, embargos, exceção de pré-executividade, Fazenda Nacional/Estadual/Municipal. Escolha 5 a 10 processos de exemplo (número CNJ, tribunal, exequente, fase, uma linha de resumo). O DJEN só cobre de meados de 2024 em diante.
- Para mapear o advogado atual do cliente (se houver), use `python3 -I /workspace/grok-bot-scripts/dossie-cliente/djen.py --oab <N> --uf <UF> --out <pasta>` (busca por OAB; gera `djen_metricas.json`).
- Dívida estadual/municipal: só fontes públicas (consulta de dívida ativa do estado, diário oficial); se exigir login, marque "não verificado" e peça ao bot dono.

**Frente C: presença e operação.** Site, Instagram (leitura pelo navegador da box, sem interagir), LinkedIn por trecho de buscador, notícias, Reclame Aqui, Google Meu Negócio, vagas abertas (sinal de porte), licitações e contratos públicos (Portal da Transparência; CND exigida), recuperação judicial ou protestos públicos.

### 3. Leitura tributária
Com os dados, responda em linguagem de reunião:
- Tamanho e composição provável do passivo (União, estado, município; previdenciário vs. demais).
- Fase de cobrança: inscrito sem execução, execução com penhora/bloqueio, risco de redirecionamento a sócios.
- Caminhos prováveis a avaliar com o Lucas: transação por adesão ou individual (Lei 13.988), parcelamento, garantia, defesa em execução, CND/CPEN. Sempre como hipótese, nunca como recomendação final.
- Urgências visíveis (leilão, bloqueio, edital com prazo, licitação que exige CND). Prazo que aparecer vai para o bot de Prazos com dupla conferência, nunca calculado aqui.

### 4. Checklist de cobertura
Cada item preenchido ou marcado "não encontrado", com fonte:
- [ ] Razão social, CNPJ, situação, abertura, CNAE, porte, regime
- [ ] Sócios e administradores; empresas ligadas
- [ ] Dívida ativa da União (valor, natureza, situação)
- [ ] Execuções fiscais e processos tributários (DJEN), com exemplos
- [ ] Dívida estadual/municipal (público ou não verificado)
- [ ] Sinais de porte e operação (site, redes, vagas, notícias)
- [ ] Dependência de CND (licitações, financiamento)
- [ ] Urgências e riscos (bloqueio, leilão, redirecionamento)
- [ ] Quem decide na empresa e quem já assessora (contador, advogado)

### 5. Roteiro da reunião (30 a 45 min, cliente fala mais)
1. Abertura: mostrar que estudamos a empresa (um dado concreto conferido).
2. Situação: confirmar o retrato (faturamento, regime, contador, débitos que ele conhece).
3. Problema: o que trava hoje (CND, bloqueio, execução, fluxo de caixa).
4. Implicação: custo de ficar como está (multa, bloqueio, perda de contrato, redirecionamento).
5. Caminhos: o que já tentou (parcelamento rompido, transação anterior).
6. Qualificação: tamanho do passivo, capacidade de pagamento, quem decide, documentos que pode mandar (procuração, relatórios do e-CAC/Regularize).
7. Próximo passo com data (envio de documentos, diagnóstico, proposta).
Cada pergunta com uma linha de "por quê" ligada a um dado do dossiê. Inclua 4 a 6 objeções prováveis com resposta (preço, "meu contador resolve", "vou esperar novo Refis", sigilo, prazo).

### 6. Entregar
Uma página (Page) ou Google Doc na pasta do cliente com: topo (empresa, CNPJ, tese de uma frase sobre o caso), perfil, passivo e processos, leitura tributária, roteiro, fontes e confiabilidade. No chat: link, 4 a 6 achados que mudam a reunião, o que confirmar na conversa e a linha "Não verificado:".
