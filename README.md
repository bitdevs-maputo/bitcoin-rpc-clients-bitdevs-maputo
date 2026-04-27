# ₿ bitcoin-rpc-clients-bitdevs-maputo

> Bibliotecas cliente em várias linguagens para a API JSON-RPC do Bitcoin Core — Python · Rust · TypeScript · Java · Go

<div align="center">
  <a href="https://www.python.org/" target="_blank">
    <img src="https://skillicons.dev/icons?i=python" height="60" alt="python logo" />
  </a>
  <a href="https://www.java.com/" target="_blank">
    <img src="https://skillicons.dev/icons?i=java" height="60" alt="java logo" />
  </a>
  <a href="https://www.typescriptlang.org/" target="_blank">
    <img src="https://skillicons.dev/icons?i=typescript" height="60" alt="typescript logo" />
  </a>
  <a href="https://rust-lang.org/" target="_blank">
    <img src="https://skillicons.dev/icons?i=rust" height="60" alt="rust logo" />
  </a>
  <a href="https://go.dev/" target="_blank">
    <img src="https://skillicons.dev/icons?i=go" height="60" alt="go logo" />
  </a>
</div>

##  Índice

- [Visão Geral](#visão-geral)
- [Funcionalidades](#funcionalidades)
- [Estrutura do Projecto](#estrutura-do-projecto)
- [Início Rápido](#início-rápido)
  - [Python](#python)
  - [Rust](#rust)
  - [TypeScript](#typescript)
  - [Java](#java)
- [Pré-requisitos](#pré-requisitos)
- [Configuração](#configuração)
- [Métodos RPC Suportados](#métodos-rpc-suportados)
- [Como Contribuir](#como-contribuir)
- [Changelog](#changelog)
- [Licença](#licença)

---

## Visão Geral

**bitcoin-rpc-clients-bitdevs-maputo** é uma colecção open source de bibliotecas cliente para interagir com a interface JSON-RPC do [Bitcoin Core](https://bitcoincore.org). Cada biblioteca é escrita nativamente na sua linguagem alvo e segue as boas práticas desse ecossistema.

Seja para construir uma carteira, um explorador de blocos, um gestor de nó Lightning ou qualquer outra aplicação Bitcoin, este projecto oferece uma base sólida e bem testada.

---

## Funcionalidades

- ✅ Cobertura completa dos métodos RPC do Bitcoin Core
- ✅ Modelos de pedido/resposta com tipos seguros em todas as linguagens
- ✅ Autenticação via HTTP Basic Auth (password e sername)
- ✅ Suporte para `regtest`, `testnet` e `mainnet`
- ✅ Suporte a `async/await` onde aplicável (Python, TypeScript, Rust)
- ✅ Suite de testes completa com nó `regtest` local
- ✅ Dependências externas mínimas

---

## Estrutura do Projecto

```
bitcoin-rpc-clients-bitdevs-maputo/
├── python/          # Biblioteca Python 
├── rust/            # Crate Rust 
├── typescript/      # Pacote TypeScript 
├── java/            # Biblioteca Java 
├── go/              # Biblioteca Go 
├── docs/            # Documentação partilhada e referência RPC
│   ├── CONTRIBUTING.md
│   ├── CHANGELOG.md
└── README.md
```

---

## Início Rápido

### Pré-requisitos

- **Bitcoin Core** ≥ 27.0 a correr localmente (ou acessível remotamente)
- `bitcoin.conf` com RPC activado:

```ini
server=1
rpcuser=o_teu_utilizador
rpcpassword=a_tua_senha
rpcport=8332
```
### Configuração via .env

Este projeto suporta configuração via ficheiro `.env` para facilitar o uso em desenvolvimento.

Cria um ficheiro .env na raiz do projeto:
Podes seguir o exemplo do [.env.local](.env.local)
---`

### [Python](/python/)

---

### [Rust](/rust/)

---

### [TypeScript](/typescript/)

---

### [Java](/java/)

---

## Configuração

| Parâmetro  | Valor Padrão            | Descrição                         |
|------------|-------------------------|-----------------------------------|
| `url`      | `http://127.0.0.1:8332` | Endpoint RPC do Bitcoin Core      |
| `user`     | —                       | Utilizador RPC                    |
| `password` | —                       | Senha RPC                         |


---

## Métodos RPC Suportados

| Categoria   | Métodos (exemplos)                                                     |
|-------------|------------------------------------------------------------------------|
| Blockchain  | `getblockchaininfo`, `getblock`, `getblockhash`, ...                   |
| Mineração   | `getmininginfo`, `getblocktemplate`, `submitblock`, ...                |
| Rede        | `getnetworkinfo`, `getpeerinfo`, `addnode`, ...                        |
| Transacções | `getrawtransaction`, `sendrawtransaction`, `decoderawtransaction`, ... |
| Carteira    | `getwalletinfo`, `getnewaddress`, `sendtoaddress`, ...                 |
| Controlo    | `getmemoryinfo`, `uptime`, `stop`, ...                                 |

Referência completa: [`docs/metodos-rpc.md`](docs/metodos-rpc.md)

---

## Como Contribuir

Contribuições de qualquer tipo são bem-vindas! Por favor lê o [CONTRIBUTING.md](/docs/contributing.md) antes de abrir um pull request.

---

## Changelog

Consulta o [CHANGELOG.md](/docs/changelog.md) para o histórico completo de versões.

---

## Licença

Este projecto está licenciado sob a **Licença MIT** — ver [LICENSE](LICENSE) para mais detalhes.

---

> **Aviso:** Este software é fornecido tal como está, para fins educativos e de desenvolvimento. Verifica sempre o comportamento em `regtest`/`testnet` antes de usar na `mainnet`.
