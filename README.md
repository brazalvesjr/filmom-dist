# FILMOM Dist

Este repositório contém os arquivos públicos necessários para instalar, atualizar e configurar o addon **FILMOM** no Kodi. A distribuição permanece enxuta: mantém somente a versão funcional atual, os índices do repositório Kodi, o instalador do repositório e as bases públicas de clientes e servidores.

## Versão atual

| Campo | Valor |
|---|---|
| Addon | `plugin.video.filmom` |
| Versão | `1.0.25` |
| Pacote principal | `plugin.video.filmom-1.0.25.zip` |
| Pacote em estrutura Kodi | `plugin.video.filmom/plugin.video.filmom-1.0.25.zip` |
| SHA-256 | `197c8dd3f517437936894846157514a3e0715bd3fc83525bdf17d62e8d736bbc` |
| Manifesto público | `manifest.json` |
| Índice Kodi | `addons.xml` |

## Arquivos mantidos

| Arquivo | Finalidade |
|---|---|
| `repository.filmom-1.0.0.zip` | Instalador do repositório FILMOM no Kodi. |
| `addons.xml` | Índice lido pelo Kodi para detectar a versão disponível do addon. |
| `addons.xml.md5` | Checksum do índice `addons.xml`. |
| `manifest.json` | Manifesto público usado pelo addon para verificar versão, pacote e hash. |
| `plugin.video.filmom-1.0.25.zip` | ZIP atual do addon, mantido na raiz para acesso direto. |
| `plugin.video.filmom/plugin.video.filmom-1.0.25.zip` | ZIP atual também mantido na estrutura por subpasta do addon, preservando compatibilidade com repositórios Kodi. |
| `plugin.video.filmom/icon.png` | Ícone público do addon. |
| `plugin.video.filmom/fanart.jpg` | Fanart público do addon. |
| `clients.json` | Base pública de clientes autorizados. |
| `servers.json` | Base pública de servidores ativos. |

## URLs públicas principais

| Recurso | URL |
|---|---|
| Instalador do repositório | `https://raw.githubusercontent.com/brazalvesjr/filmom-dist/main/repository.filmom-1.0.0.zip` |
| ZIP atual na raiz | `https://raw.githubusercontent.com/brazalvesjr/filmom-dist/main/plugin.video.filmom-1.0.25.zip` |
| ZIP atual na estrutura Kodi | `https://raw.githubusercontent.com/brazalvesjr/filmom-dist/main/plugin.video.filmom/plugin.video.filmom-1.0.25.zip` |
| Índice Kodi | `https://raw.githubusercontent.com/brazalvesjr/filmom-dist/main/addons.xml` |
| Checksum do índice | `https://raw.githubusercontent.com/brazalvesjr/filmom-dist/main/addons.xml.md5` |
| Manifesto | `https://raw.githubusercontent.com/brazalvesjr/filmom-dist/main/manifest.json` |
| Clientes | `https://raw.githubusercontent.com/brazalvesjr/filmom-dist/main/clients.json` |
| Servidores | `https://raw.githubusercontent.com/brazalvesjr/filmom-dist/main/servers.json` |

## Observações da versão 1.0.25

A versão **1.0.25** mantém o player nativo único da v1.0.24 e foca em desempenho de navegação. Ela adiciona cache local para respostas da API Xtream, reduz chamadas remotas repetidas de clientes e servidores, limita a frequência do verificador de atualização e usa timeout padrão menor para evitar esperas longas ao abrir listas ou retornar de filmes.

## Política de organização

Este repositório deve permanecer enxuto. Versões antigas do addon não devem ser mantidas indefinidamente no branch principal, salvo quando houver necessidade explícita de rollback. Para a operação normal do Kodi, a referência ativa é sempre a versão declarada em `addons.xml` e `manifest.json`.
