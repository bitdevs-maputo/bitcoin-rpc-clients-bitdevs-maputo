# Changelog

Todas as alterações notáveis ao **bitcoin-rpc-clients-bitdevs-maputo** serão documentadas neste ficheiro.

Este projecto segue o [Versionamento Semântico](https://semver.org/) e o formato é baseado em [Keep a Changelog](https://keepachangelog.com/).

---

## [Não Lançado]

> Alterações já incorporadas em `main` mas ainda não publicadas numa versão oficial.

### Adicionado
- (as tuas próximas alterações vão aqui)

---

## [0.1.0] — 2026-04-25

### Adicionado

#### Python
- Lançamento inicial da biblioteca Python `bitcoin-rpc`
- Cliente síncrono `BitcoinRPC` usando ``
- Cliente assíncrono `AsyncBitcoinRPC` com suporte a ``
- Suporte a autenticação por username e password
- Métodos RPC implementados:
  - `getblockchaininfo`, `getbestblockhash`, `getblockhash`, `getblock`
  - `getrawtransaction`, `sendrawtransaction`, `decoderawtransaction`
  - `getnetworkinfo`, `getpeerinfo`
  - `getmininginfo`, `getblocktemplate`
  - `getwalletinfo`, `getnewaddress`, `sendtoaddress`, `listunspent`
  - `uptime`, `getmemoryinfo`

#### Rust
- Lançamento inicial do crate `bitcoin-rpc-client`
- Cliente assíncrono construído com `` + `reqwest`
- Structs com tipos fortes para pedidos/respostas de todos os métodos suportados
- Mesma cobertura de métodos RPC que a biblioteca Python

#### TypeScript
- Lançamento inicial do pacote npm `bitcoin-rpc-clients-bitdevs-maputo`
- Classe `BitcoinRPC` com suporte a `async/await` usando `fetch` nativo
- Tipos TypeScript completos para todos os parâmetros e respostas RPC
- Suporta Node.js ≥ 20 e bundlers modernos


#### Java
- Lançamento inicial do artefacto Maven `bitcoin-rpc-client`
- `BitcoinRpcClient` construído com `OkHttp` + `Jackson`
- Padrão Builder para a construção do cliente
- Mesma cobertura de métodos RPC que as outras bibliotecas

#### Go
- Lançamento inicial da biblioteca Go `bitcoin-rpc-client`
- Cliente construído com `net/http` da biblioteca padrão
- Suporte a autenticação HTTP Basic Auth e por cookie
- Mesma cobertura de métodos RPC que as outras bibliotecas


#### Projecto / Infraestrutura
- Estrutura monorepo com sub-projectos `python/`, `rust/`, `typescript/`, `java/`, `go/`
- Pasta `docs/` com documentação partilhada e referência de métodos RPC
- `.gitignore` com entradas para todas as linguagens (build, cache, dependências, artefactos)
- `README.md` com badges de ícones para cada linguagem via [skillicons.dev](https://skillicons.dev)
- `CONTRIBUTING.md` com guia para adicionar novas linguagens, padrões de Código Limpo e Conventional Commits
- `CHANGELOG.md` e `CODE_OF_CONDUCT.md`
- Licença MIT

---

