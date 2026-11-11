# Insanity Games — SaaS starter

## Testar agora
Abra `index.html` no navegador. A interface é uma demonstração local, sem login nem cobranças reais. Ela foi ampliada para simular múltiplas academias e campeonatos.

## Banco de dados
`database/schema.sql` fornece a estrutura multi-tenant inicial para Supabase PostgreSQL, com isolamento por organização e políticas RLS. Execute em um projeto de testes do Supabase. Não conecte o protótipo estático diretamente a tabelas privilegiadas.

## Para colocar em produção
1. Implementar autenticação Supabase e fluxo de criação de organizações com proprietário autenticado, em transação no servidor.
2. Implementar API de inscrições com validação de categoria, preço, limites de vagas, proteção anti-spam e consentimento LGPD.
3. Integrar gateway de pagamento brasileiro (Pix e cartão) com checkout seguro, webhooks autenticados e idempotentes; somente o servidor altera status `paid`.
4. Criar rotas autenticadas para resultados e baterias; implementar súmulas, auditoria de alterações e controle de permissões de árbitros.
5. Criar view ou RPC de leaderboard que particione por categoria, trate empates, cap, DNF/DNS, critérios de desempate e tabelas configuráveis de pontos.
6. Implementar atualizações em tempo real, testes de isolamento de organizações, logs, backups e publicação na Vercel.

**Atenção:** o SQL é uma base de modelagem, não um produto de pagamentos pronto. Revisar autorização e integridade de `heat_lanes`, criação de tenants, regras de pontuação e exposição de dados antes da produção.

## Modelo comercial aprovado (ainda não ativado)
- 0–10 inscrições confirmadas por campeonato: START, grátis.
- 11–15: faixa de transição grátis (lacuna preenchida provisoriamente).
- 16–30: PRO, taxa de R$ 3,00 apenas por inscrição adicional acima da 15ª.
- 31+: PREMIUM, mensalidade de R$ 99,90, substituindo a taxa por inscrição.
- Cada inscrição individual, dupla ou equipe conta como uma unidade; não contar pessoas dentro da equipe separadamente.
- As tarifas do gateway não estão incluídas.
- Preços, cancelamentos, reembolsos, período de cobrança e transição entre planos exigem aprovação antes da integração real.
- Aba **Planos e cobrança** permite simular os valores, sem criar cobrança.

## Revisão de 11/11/2026
- Corrigido o cálculo de colocação dos WODs para separar atletas por categoria mesmo ao selecionar “Todas”.
- Corrigido o texto da aba de cobrança para refletir os valores aprovados.
- O ZIP foi reorganizado com `index.html` na raiz para facilitar o deploy estático na Vercel.
- Atenção: este protótipo usa `localStorage`, não oferece isolamento real entre usuários, e não pode receber inscrições pagas ou dados pessoais reais.
- O esquema SQL é apenas ponto de partida e requer revisão de segurança antes de uso em produção.
