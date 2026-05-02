# FILMOM distribuição pública

Este repositório contém os arquivos públicos necessários para distribuição e atualização do addon **FILMOM** para Kodi.

A versão publicada atualmente é a **1.0.7**. Esta versão foi reconstruída no mesmo padrão funcional do repositório de referência `plugn-streaming-vip-repo`, usando autenticação simples por `clients.json` e carregamento de servidores por `servers.json`, sem o fluxo anterior de senha criptografada/protegida.

| Arquivo | Função |
|---|---|
| `manifest.json` | Manifesto de atualização automática apontando para a versão mais recente. |
| `plugin.video.filmom-1.0.7.zip` | Pacote instalável final do addon FILMOM para Kodi. |
| `plugin.video.filmom-1.0.7.zip.sha256` | Hash SHA-256 para verificação de integridade do ZIP. |
| `clients.json` | Lista simples de clientes autorizados, com `password` e `active`. |
| `servers.json` | Lista simples de servidores ativos, com `url`, `user`, `pass` e `active`. |
| `icon.png` | Ícone quadrado 512x512 corrigido para o addon. |

> Para evitar conflito com dados antigos das versões 1.0.3 a 1.0.6, recomenda-se instalar a versão 1.0.7 após limpar/remover os dados antigos do addon FILMOM no Kodi.
