# Coleta de Resultados dos Simulados — URE Sumaré

Aplicação estática para GitHub Pages. A autenticação e os registros compartilhados usam o projeto Supabase `simulados`.

## Publicar no GitHub Pages

1. Crie um repositório GitHub chamado `coleta-simulados-ure-sumare` e envie estes arquivos para a branch `main`.
2. No repositório, abra **Settings → Pages** e selecione **GitHub Actions** como fonte de publicação.
3. O workflow `.github/workflows/pages.yml` publica `index.html` a cada envio para `main`. O endereço ficará no formato `https://SEU-USUARIO.github.io/coleta-simulados-ure-sumare/`.
4. No Supabase, defina esse endereço como **Site URL** e acrescente-o às URLs permitidas de redirecionamento em **Authentication → URL Configuration**.
5. Configure um SMTP institucional em **Authentication → SMTP** antes de liberar o login por e-mail às escolas.

## Dados e segurança

- O repositório contém a interface e o SQL de referência; não contém dados coletados.
- O banco Supabase usa RLS: usuários verificados dos domínios institucionais permitidos consultam os registros compartilhados; somente o autor pode excluir os próprios registros.
- A chave `sb_publishable` no cliente é pública e limitada pelas políticas do banco. Nunca adicione chaves `service_role`, senhas SMTP, tokens privados ou arquivos `.env` ao repositório.
- O arquivo em `supabase/migrations/` documenta o esquema e as políticas já aplicadas no projeto Supabase `simulados`. Não execute novamente sobre esse projeto já configurado.

## Desenvolvimento

Abra `index.html` por um servidor HTTP local ou pelo GitHub Pages. O login por e-mail redireciona de volta ao endereço hospedado configurado no Supabase.
