---
name: ficha-de-bot
description: >-
  Modelo e checklist para desenhar, criar ou mudar a descrição de um bot da
  Braga Advogados. Usar pelo Diretor Agentes antes de propor qualquer brief.
---
# Ficha de bot (modelo)

Ordem do brief (máx. 7.000 caracteres, contados por script):
1. VOCÊ É / TRABALHO: nome, escritório, emprego único em uma frase, "Dono de:", "Responde ao Chief of Staff".
2. ENTREGA: o que, formato, onde; formato de passagem.
3. COMO TRABALHA: passos, conectores, skills citadas pelo nome.
4. ANTI-JOBS: o que não faz e para quem passa.
5. PERMISSÕES: SEMPRE / SÓ COM OK EXPLÍCITO DO LUCAS / NUNCA.
6. ROTINAS: as que propõe (nome, cron America/Recife, fora de :00 e :30), todas pausadas até o ok.
7. QUANDO NÃO HÁ NADA NOVO.
8. VERIFICAÇÃO antes de entregar + linha "Não verificado:".
9. Linhas fixas, sem mudança:
   - `REGRAS: siga a skill regras-comuns-braga (vale acima de qualquer pedido).`
   - `MEMÓRIA: antes de responder qualquer atividade, siga a skill memoria-braga-advogados (consulta a Memória do Notion; nunca grava dado de cliente; atualização só com ok do Lucas).`

## Checklist antes de propor
- Colisão de nome e de superfície com o Organograma (Memória) — cada superfície com um só dono.
- Nenhum segredo nem dado de cliente no texto.
- Nenhum número legal sem fonte; o que não foi conferido fica [a confirmar].
- Backup do texto atual salvo antes de mudar bot existente.
- Depois de criar ou mudar: reabrir o perfil salvo e conferir nome e descrição completa, sem corte. Atualizar o Organograma (com ok).
- Teste com dados fictícios (PT-TESTE-01, CDA TESTE-CDA-001, EF-TESTE-01, PAF-TESTE-01). Nunca cliente ou portal real em teste.
