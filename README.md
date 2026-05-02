# FILMOM Dist

Este repositório publica os arquivos de distribuição do addon **FILMOM** para Kodi. O FILMOM é um addon independente e usa uma base própria de clientes em `clients.json`, sem herdar nomes, senhas ou regras de outro addon.

## Versão atual

| Campo | Valor |
|---|---|
| Addon | `plugin.video.filmom` |
| Versão | `1.0.8` |
| ZIP | `plugin.video.filmom-1.0.8.zip` |
| Configuração de clientes | `clients.json` |
| Configuração de servidores | `servers.json` |

## Como cadastrar clientes

O arquivo `clients.json` publicado aqui está propositalmente em formato **modelo/vazio**. Isso significa que nenhum cliente real é liberado até você cadastrar senhas próprias para sua operação.

Para liberar um cliente, edite `clients.json` e adicione registros dentro da lista `clients`, seguindo este formato:

```json
{
  "schema": "filmom-clients-v1",
  "version": "1",
  "clients": [
    {
      "id": "001",
      "name": "Cliente 001",
      "password": "senha-do-cliente-001",
      "active": true,
      "expires": "2026-12-31"
    }
  ]
}
```

O addon valida a senha digitada pelo campo `password`. Também aceita os aliases `senha` ou `pass` caso você prefira esses nomes. Para bloquear um cliente sem apagar o cadastro, altere `active` para `false`.

## Arquivos públicos

| Arquivo | URL |
|---|---|
| ZIP | https://raw.githubusercontent.com/brazalvesjr/filmom-dist/main/plugin.video.filmom-1.0.8.zip |
| Manifesto | https://raw.githubusercontent.com/brazalvesjr/filmom-dist/main/manifest.json |
| Clientes | https://raw.githubusercontent.com/brazalvesjr/filmom-dist/main/clients.json |
| Servidores | https://raw.githubusercontent.com/brazalvesjr/filmom-dist/main/servers.json |

## Observação operacional

Com a base vazia, o Kodi exibirá aviso informando que não há clientes cadastrados no `clients.json`. Isso é esperado. Depois que você adicionar pelo menos um cliente ativo com senha, o FILMOM passará a liberar o acesso para essa senha.
