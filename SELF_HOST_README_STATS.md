# Self-host github-readme-stats (guia rápido)

As estatísticas no README podem falhar quando o serviço público `github-readme-stats.vercel.app` está sobrecarregado ou rate-limited. A solução mais confiável é self-hostear o projeto e apontar suas imagens para a sua instância no Vercel.

Passos resumidos (eu posso fazer parte deles se você me autorizar):

1) Fork do projeto oficial
- Vá para: https://github.com/anuraghazra/github-readme-stats
- Clique em "Fork" e escolha sua conta (Saulorangel87). Agora terá `https://github.com/Saulorangel87/github-readme-stats`.

2) Deploy no Vercel
- Acesse https://vercel.com/ e faça login com sua conta GitHub (ou crie uma conta).
- Clique em "New Project" → "Import Git Repository" e selecione o fork `Saulorangel87/github-readme-stats`.
- Aceite as configurações padrão. Opcionalmente defina o nome do projeto para `github-readme-stats` (para ter uma URL previsível).
- Clique em "Deploy". O Vercel criará uma URL do tipo `https://<project-name>-<git-user>.vercel.app`.

3) Teste a URL da sua instância
- Supondo que a URL gerada seja `https://github-readme-stats-saulorangel87.vercel.app`, teste no terminal:

  curl -I "https://github-readme-stats-saulorangel87.vercel.app/api?username=Saulorangel87&theme=dark&show_icons=true&hide_border=false"

  Deve retornar HTTP/200 e Content-Type: image/svg+xml.

4) Atualizar seu README
- Substitua as URLs existentes por:

  https://github-readme-stats-saulorangel87.vercel.app/api?username=Saulorangel87&theme=dark&show_icons=true&hide_border=false&cache_seconds=1800

  https://github-readme-stats-saulorangel87.vercel.app/api/top-langs/?username=Saulorangel87&theme=dark&layout=compact&hide_border=false&cache_seconds=1800

- Eu posso fazer esse commit para você assim que me der a URL exata gerada pelo Vercel.

5) Opção avançada: deploy automático (CI)
- Se você quiser, podemos criar uma GitHub Action para redeployar a cada push. Não é necessário para começar.

6) Privacidade/repos privados
- Se seus repositórios forem privados, configure um token GitHub na variável de ambiente `GITHUB_TOKEN` do Vercel (ou um PAT com acesso a `repo`) e configure o fork para usar esse token para coletar estatísticas.

O que eu já fiz
- Corrigi seu README para usar seu username correto e adicionei `cache_seconds=1800` (commit já feito). Essa correção é necessária mas não resolve downtime do serviço público.

O que eu preciso de você para completar a solução confiável
- Confirme se quer que eu:
  a) Crie instruções/documento (já adicionei este arquivo).  
  b) Faça o fork do repo `anuraghazra/github-readme-stats` na sua conta (para isso preciso que você me autorize a criar repositórios no seu GitHub — não posso sem permissões).  
  c) Depois que você fizer o deploy no Vercel, me passe a URL final e eu atualizo o README automaticamente com essa URL.

Se quiser, eu posso guiar passo a passo enquanto você faz o fork e o deploy — diga por onde quer começar. Se preferir, cole aqui a URL de deploy do Vercel e eu atualizo o README agora.