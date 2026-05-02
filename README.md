# FILMOM Dist

Este repositório contém somente os arquivos públicos necessários para distribuir e configurar o addon **FILMOM** para Kodi. A distribuição foi reorganizada para manter a versão atual do pacote, o manifesto de atualização e as bases próprias de clientes e servidores, sem arquivos herdados de outros addons.

## Versão atual

| Campo | Valor |
|---|---|
| Addon | `plugin.video.filmom` |
| Versão | `1.0.9` |
| Pacote | `plugin.video.filmom-1.0.9.zip` |
| Hash SHA-256 | `bada7deba526662a44c845836248c5dc363820386c6d7289e9eff1f0ee8b857f` |
| Manifesto | `manifest.json` |

## Arquivos publicados

| Arquivo | Finalidade |
|---|---|
| `plugin.video.filmom-1.0.9.zip` | Pacote instalável da versão atual do addon. |
| `plugin.video.filmom-1.0.9.zip.sha256` | Verificação de integridade do pacote atual. |
| `manifest.json` | Informa a versão disponível, a URL do ZIP e o hash SHA-256. |
| `clients.json` | Controla os clientes e senhas autorizados para acessar o addon. |
| `servers.json` | Define a base própria de servidores do FILMOM. A lista começa vazia para não herdar dados de outro addon. |

## URLs públicas

| Recurso | URL |
|---|---|
| ZIP atual | https://raw.githubusercontent.com/brazalvesjr/filmom-dist/main/plugin.video.filmom-1.0.9.zip |
| Hash SHA-256 | https://raw.githubusercontent.com/brazalvesjr/filmom-dist/main/plugin.video.filmom-1.0.9.zip.sha256 |
| Manifesto | https://raw.githubusercontent.com/brazalvesjr/filmom-dist/main/manifest.json |
| Clientes | https://raw.githubusercontent.com/brazalvesjr/filmom-dist/main/clients.json |
| Servidores | https://raw.githubusercontent.com/brazalvesjr/filmom-dist/main/servers.json |

## Clientes

O arquivo `clients.json` libera acesso quando a senha digitada corresponde a um cliente ativo. A base atual contém dois clientes de exemplo para teste.

| ID | Nome | Senha | Ativo | Expira |
|---|---|---|---|---|
| `001` | Cliente Exemplo 001 | `senha001` | `true` | `2026-12-31` |
| `002` | Cliente Exemplo 002 | `senha002` | `true` | `2026-12-31` |

## Servidores

O arquivo `servers.json` foi reiniciado como uma base independente do FILMOM. Ele permanece com `servers: []` até que servidores reais sejam cadastrados. O addon 1.0.9 também limpa servidores herdados do perfil local quando a base pública não possui servidores ativos.

Para cadastrar um servidor real, use o formato abaixo dentro da lista `servers`:

```json
{
  "schema": "filmom-servers-v1",
  "version": "1",
  "servers": [
    {
      "id": 1,
      "name": "Servidor 1",
      "url": "http://seu-servidor.com:80",
      "user": "usuario-do-servidor",
      "pass": "senha-do-servidor",
      "active": true
    }
  ]
}
```

## Observações da versão 1.0.9

A versão **1.0.9** remove a herança dos quinze servidores de outro addon, limpa servidores antigos quando `servers.json` estiver vazio e força a atualização da interface após a senha ser aceita. Com isso, o usuário não deve mais precisar voltar manualmente para visualizar a tela principal do FILMOM.
