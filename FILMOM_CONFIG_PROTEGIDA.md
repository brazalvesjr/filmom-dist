# FILMOM 1.0.3 — Configuração pública protegida

A versão **1.0.3** corrige a limitação operacional encontrada na versão 1.0.2: arquivos `raw.githubusercontent.com` de repositórios privados não podem ser baixados por clientes Kodi sem autenticação. Como o Kodi instalado no dispositivo do cliente precisa buscar `clientes.json`, `manifest.json` e o ZIP de atualização sem login no GitHub, a distribuição remota deve ficar em uma URL pública.

> O objetivo da correção é permitir hospedagem pública do `clientes.json` sem publicar diretamente URL, usuário e senha do servidor em texto aberto.

## Novo modelo de dados

O `clientes.json` público passa a usar entradas protegidas. Cada cliente possui metadados simples, como `id`, `active` e `expires`, e um bloco `protected_config` contendo um pacote codificado em Base64. Esse pacote inclui os servidores e demais dados sensíveis criptografados a partir da senha que o próprio cliente digita na abertura do addon.

| Campo | Visível no JSON público | Observação |
|---|---:|---|
| `id` | Sim | Identificador administrativo do cliente. |
| `active` | Sim | Permite bloquear ou liberar o cliente remotamente. |
| `expires` | Sim | Data de expiração em formato `AAAA-MM-DD`. |
| `protected_config` | Sim, porém codificado | Contém servidores, URL, usuário e senha em forma protegida. |
| URL/usuário/senha do servidor | Não em texto aberto | São recuperados localmente somente após a senha correta. |

## Fluxo no Kodi

Ao abrir o addon, o FILMOM baixa o `clientes.json` público e exibe **DIGITE A SENHA DO CLIENTE**. Em vez de comparar a senha contra um campo público, o addon tenta descriptografar cada cliente ativo com a senha informada. Se a descriptografia gerar um pacote FILMOM válido, o acesso é liberado e os servidores descriptografados ficam salvos apenas no perfil local do Kodi.

| Etapa | Comportamento |
|---|---|
| Download | O addon baixa o JSON público sem token GitHub. |
| Senha | O usuário digita apenas a senha do cliente. |
| Validação | O addon tenta abrir o pacote protegido correspondente. |
| Servidores | A interface mostra somente números: `1`, `2`, `3`. |
| Credenciais | URL, usuário e senha não aparecem na interface. |

## Limite de segurança

Esta arquitetura evita credenciais em texto aberto no JSON público, mas não substitui um servidor backend autenticado. Como todo addon instalado no cliente contém o código necessário para abrir a configuração, usuários avançados ainda podem tentar engenharia reversa. Por isso, as senhas dos clientes devem ser fortes e únicas, e clientes bloqueados devem ser removidos ou marcados como inativos no JSON remoto.

