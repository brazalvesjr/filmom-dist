# FILMOM 1.0.3 — Instruções administrativas

A versão **FILMOM 1.0.3** foi ajustada para funcionar com um `clientes.json` público protegido. O Kodi do cliente não consegue baixar arquivos `raw.githubusercontent.com` de um repositório privado sem autenticação, por isso os arquivos de distribuição devem ficar em um repositório público ou em outra hospedagem pública. A diferença desta versão é que o JSON público **não contém URL, usuário e senha do servidor em texto aberto**.

> Publique no repositório público apenas `clientes.json`, `manifest.json`, o ZIP do addon e os assets necessários. Mantenha o arquivo administrativo em texto claro fora do repositório público.

## Arquivos principais

| Arquivo | Uso | Deve ser público? |
|---|---|---:|
| `clientes_plain.example.json` | Modelo administrativo em texto claro para você editar. | Não. |
| `gerar_clientes_protegido.py` | Script que transforma o arquivo administrativo em `clientes.json` protegido. | Não precisa. |
| `clientes.json` | Arquivo protegido que o Kodi baixa ao abrir o addon. | Sim. |
| `manifest.json` | Arquivo de atualização automática. | Sim. |
| `plugin.video.filmom-1.0.3.zip` | ZIP instalável ou baixado pelo atualizador. | Sim. |

## Como cadastrar cliente e servidor

Edite uma cópia privada do arquivo administrativo, usando o formato abaixo. Cada cliente deve ter uma senha forte e única. Os servidores podem ficar no topo do arquivo, valendo para todos os clientes, ou dentro de um cliente específico se você quiser liberar servidores diferentes por cliente.

```json
{
  "enabled": true,
  "message": "Acesso FILMOM liberado.",
  "clients": [
    {
      "id": "cliente_teste",
      "senha": "SENHA-FORTE-DO-CLIENTE",
      "active": true,
      "expires": "2099-12-31"
    }
  ],
  "servers": [
    {
      "number": 1,
      "url": "https://seu-servidor.com",
      "username": "usuario_do_servidor",
      "password": "senha_do_servidor",
      "active": true
    }
  ]
}
```

Depois gere o JSON público protegido com:

```bash
python3.11 gerar_clientes_protegido.py clientes_plain.json clientes.json
```

O arquivo `clientes.json` gerado pode ser publicado em uma URL pública. O cliente abrirá o addon, verá a mensagem **DIGITE A SENHA DO CLIENTE**, digitará a senha cadastrada, e o addon tentará abrir o pacote protegido correspondente. Se a senha estiver correta e o cliente estiver ativo, o acesso será liberado.

## Bloqueio de cliente

Para bloquear um cliente, altere `active` para `false` no arquivo administrativo, gere novamente o `clientes.json` protegido e publique o novo arquivo. Na próxima validação, o addon recusará o cliente bloqueado.

```json
{
  "id": "cliente_teste",
  "senha": "SENHA-FORTE-DO-CLIENTE",
  "active": false,
  "expires": "2099-12-31"
}
```

## Observação de segurança

Esta solução remove as credenciais em texto aberto do JSON público e exige a senha do cliente para abrir o pacote localmente. Ainda assim, por se tratar de um addon instalado no dispositivo do cliente, não é equivalente a um backend privado com autenticação no servidor. Use senhas fortes por cliente, bloqueie clientes individualmente quando necessário e evite reutilizar a mesma senha para todos.
