# Insanity Games — autenticação Supabase (Next.js)
Este pacote substitui o protótipo HTML e adiciona login real, criação de conta, recuperação de senha e leitura de eventos publicados do Supabase. **Não** implementa ainda inscrições, gestão de eventos ou pagamentos reais.
## Publicação
1. Crie uma branch ou repositório Git com estes arquivos, preservando `app/` na raiz.
2. Na Vercel, importe esse repositório ou faça push ao repositório já conectado ao projeto. Framework: Next.js.
3. Configure `NEXT_PUBLIC_SUPABASE_URL` e `NEXT_PUBLIC_SUPABASE_PUBLISHABLE_KEY` no ambiente Production.
4. Faça deploy e confirme que o formulário de login aparece.
5. No Supabase, configure Authentication > URL Configuration para o domínio real.
6. Crie um usuário e confirme seu e-mail; faça login. A conta ainda não será vinculada automaticamente a uma academia.
## Segurança
Não coloque service_role, tokens de Mercado Pago ou senhas em código do cliente. O endpoint `/api/public-config` retorna apenas os dois valores públicos. Não execute scripts SQL antigos novamente. Antes de implementar operações de escrita, crie autorização no servidor, auditoria e políticas adequadas.
