# Insta Discord

Bot de comunidade com uma rede social inspirada no Instagram, funcionando inteiramente dentro do Discord. As publicações e interações são separadas por servidor e ficam persistidas em SQLite.

## Recursos

- `/criar-conta` e `/editar-perfil`: crie sua conta e personalize seu @usuário e biografia. Os @usuários são exclusivos dentro de cada servidor.
- `/postar`: publique uma legenda, uma imagem, um vídeo ou uma combinação deles.
- `/feed`: navegue por publicações recentes de todo o servidor ou escolha **Seguindo** para ver contas que você segue. Curta, salve e reposte pelos botões.
- `/explorar` e `/buscar-perfil`: descubra posts populares e encontre contas pelo @usuário.
- `/curtir`, `/comentar` e `/comentarios`: interaja com os posts pelo número exibido no feed.
- `/repostar`: compartilhe novamente uma publicação, com legenda opcional.
- `/perfil`, `/seguir` e `/deixar-de-seguir`: consulte perfis e mantenha sua rede no servidor.
- `/salvar-post` e `/posts-salvos`: guarde publicações para consultar depois.
- `/apagar-post`: apague sua publicação; moderadores com **Gerenciar mensagens** também podem remover posts de outros usuários.
- `/configurar-feed`: escolha o canal público para novas publicações. Sem configuração, o bot usa o canal em que `/postar` ou `/repostar` foi executado.

Crie sua conta com `/criar-conta` antes de postar ou usar as interações sociais. Contas, publicações e seguidores são independentes em cada servidor.

## Instalação

Requisitos: Node.js 20 ou superior e uma aplicação/bot criado no [Discord Developer Portal](https://discord.com/developers/applications).

1. Instale as dependências:

   ```powershell
   npm install
   ```

2. Copie `.env.example` para `.env` e preencha `DISCORD_TOKEN` e `DISCORD_CLIENT_ID`. Opcionalmente, informe `DISCORD_GUILD_ID` para registrar os comandos apenas no servidor de testes — a atualização costuma ser mais rápida.
3. Convide o bot para o servidor com os escopos `bot` e `applications.commands` e permissão para ver canais, enviar mensagens, ler o histórico, incorporar links e anexar arquivos.
4. Registre os comandos e inicie o bot:

   ```powershell
   npm run register-commands
   npm start
   ```

O bot precisa da permissão **Gerenciar servidor** para executar `/configurar-feed`. Sem um canal configurado, ele publica no canal do comando. As permissões para visualizar e publicar também precisam estar liberadas para o bot nesse canal.

Depois de adicionar ou alterar comandos, execute novamente `npm run register-commands` e faça um novo deploy para que o Discord atualize a lista de comandos.

## Dados e testes

Por padrão, o banco é criado em `data/insta-discord.sqlite`; defina `DATABASE_PATH` para usar outro caminho. Faça cópias desse arquivo para preservar os dados. Para executar os testes:

```powershell
npm test
```

O bot não publica no Instagram real nem acessa contas ou conteúdo de lá; uploads e reposts são feitos nos canais do Discord onde ele está instalado.
