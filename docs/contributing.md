# Como Contribuir para o bitcoin-rpc-clients-bitdevs-maputo-bitdevs-maputo

Obrigado pelo teu interesse em contribuir! 
Há duas formas principais de contribuir para este projecto:

1. **Adicionar suporte a uma nova linguagem de programação**
2. **Melhorar uma implementação já existente**
3. **Atualizar o `.gitignore` para incluir ficheiros específicos da nova linguagem (build, cache, dependências, artefactos)**

Todas as contribuições devem seguir os nossos padrões de [Código Limpo](#padrões-de-código-limpo) e a convenção de [Conventional Commits](#mensagens-de-commit).

---

## Índice`

- [Código de Conduta](#código-de-conduta)
- [Como Contribuir](#como-contribuir)
  - [Opção A — Abrir uma Issue](#opção-a--abrir-uma-issue)
  - [Opção B — Abrir um Pull Request](#opção-b--abrir-um-pull-request)
- [Adicionar uma Nova Linguagem](#adicionar-uma-nova-linguagem)
  - [Checklist para Nova Linguagem](#checklist-para-nova-linguagem)
  - [Estrutura de Pastas](#estrutura-de-pastas)
  - [Métodos RPC Obrigatórios](#métodos-rpc-obrigatórios)
- [Melhorar uma Linguagem Existente](#melhorar-uma-linguagem-existente)
- [Padrões de Código Limpo](#padrões-de-código-limpo)
- [Mensagens de Commit](#mensagens-de-commit)
- [Processo de Pull Request](#processo-de-pull-request)
- [Reportar Problemas](#reportar-problemas)

---

## Código de Conduta

Ao participar neste projecto concordas em respeitar o nosso [Código de Conduta](CODE_OF_CONDUCT.md). Trata toda a gente com respeito.

---

## Como Contribuir

### Opção A — Abrir uma Issue

Usa uma issue quando quiseres:

- **Propor uma nova linguagem** antes de escrever código (recomendado — evita esforço duplicado)
- **Reportar um problema** numa implementação existente
- **Sugerir uma melhoria** sem submeteres código
- **Fazer uma pergunta** sobre a arquitectura ou decisões de desenho


---

### Opção B — Abrir um Pull Request

Usa um pull request quando tens código funcional pronto para revisão. Um PR pode:

- Adicionar uma nova implementação numa linguagem
- Corrigir um problema numa biblioteca existente
- Melhorar desempenho, tratamento de erros ou qualidade de código
- Adicionar ou corrigir testes
- Actualizar documentação


Podes também **abrir um PR em modo draft** para partilhar progresso e receber feedback antes de a implementação estar completa.

---

## Adicionar uma Nova Linguagem

Queres adicionar Go, C#, Kotlin, Elixir ou outra linguagem? Óptimo — segue os passos abaixo.

### Antes de Começar

1. Abre uma `issue` para anunciar a nova linguagem, para que os maintainers possam confirmar que não há esforço duplicado.
2. Aguarda que um maintainer coloque a etiqueta `aceite` na issue antes de investires tempo significativo.

### Checklist para Nova Linguagem

- [ ] Criar a pasta `<linguagem>/` na raiz do repositório
- [ ] Seguir a [estrutura de pastas](#estrutura-de-pastas) definida abaixo
- [ ] Implementar todos os [métodos RPC obrigatórios](#métodos-rpc-obrigatórios)
- [ ] Disponibilizar clientes síncrono e assíncrono (se a linguagem suportar)
- [ ] Suportar autenticação HTTP Basic Auth com utilizador e senha
- [ ] Escrever pelo menos um teste de integração contra um nó `regtest`
- [ ] Adicionar um `README.md` dentro da pasta da linguagem com:
  - Instruções de instalação
  - Exemplo de código de início rápido
  - Como correr os testes
- [ ] Adicionar a nova linguagem na secção de badges e início rápido do `README.md` raiz
- [ ] Atualizar o `.gitignore` para incluir ficheiros específicos da nova linguagem
- [ ] Actualizar o `CHANGELOG.md` na secção `[Não Lançado]`

### Estrutura de Pastas

Cada linguagem deve seguir esta organização:

```
<linguagem>/
├── src/                  # Código fonte
│   ├── client.{ext}      # Classe / módulo principal do cliente RPC
│   ├── methods/          # Um ficheiro por categoria RPC (blockchain, carteira, rede, ...)
│   └── models/           # Tipos, structs ou classes de pedido e resposta
├── tests/                # NB: Opcional
│   ├── unit/             # Testes unitários (sem nó Bitcoin necessário)
│   └── integration/      # Testes de integração (requer nó regtest)
├── examples/             # Exemplos curtos de utilização
├── README.md             # Documentação específica da linguagem
└── <manifesto-pacote>    # Ex: package.json, Cargo.toml, pom.xml, go.mod ...
```

### Métodos RPC Obrigatórios

Uma nova implementação deve cobrir no mínimo os seguintes métodos antes de o PR poder ser aceite:

| Categoria   | Métodos                                                              |
|-------------|----------------------------------------------------------------------|
| Blockchain  | `getblockchaininfo`, `getbestblockhash`, `getblockhash`, `getblock` |
| Rede        | `getnetworkinfo`, `getpeerinfo`                                      |
| Mineração   | `getmininginfo`, `getblocktemplate`                                  |
| Transacção  | `getrawtransaction`, `sendrawtransaction`, `decoderawtransaction`    |
| Carteira    | `getwalletinfo`, `getnewaddress`, `sendtoaddress`, `listunspent`     |
| Controlo    | `uptime`, `getmemoryinfo`                                            |

Métodos adicionais para além desta base são sempre bem-vindos.

---

## Melhorar uma Linguagem Existente

Para melhorar Python, Rust, TypeScript ou Java:

- **Correcção de problema** — abre uma issue a descrever o problema, depois submete um PR com um teste que o reproduz e a correcção.
- **Novo método RPC** — consulta a [referência RPC](docs/metodos-rpc.md), implementa o método seguindo os padrões existentes nessa biblioteca e inclui testes.
- **Refactoring / desempenho** — abre uma issue primeiro para discutir a abordagem antes de fazer grandes alterações.
- **Documentação** — PRs que só actualizam documentação ou exemplos são aceites sem issue prévia.

---

## Padrões de Código Limpo

Todo o código — independentemente da linguagem — deve seguir estes princípios:

**Nomenclatura**
- Usa nomes claros e descritivos para variáveis, funções e classes.
- Evita abreviações excepto as universalmente compreendidas (ex: `rpc`, `url`, `tx`).

**Funções**
- Cada função faz uma única coisa.
- As funções devem ser curtas e fáceis de ler sem ter de fazer scroll.
- Evita efeitos secundários sempre que possível.

**Tratamento de Erros**
- Nunca ignores erros silenciosamente.
- Fornece mensagens de erro claras que ajudem o chamador a perceber o que correu mal.
- Usa os mecanismos de tratamento de erros nativos de cada linguagem (excepções, `Result`, `Either`, etc.).

**Tipos**
- Todas as APIs públicas devem estar totalmente tipadas.
- Não uses `any`, `Object` ou mapas sem tipo em interfaces públicas.

**Testes**
- Cada método público deve ter pelo menos um teste unitário.
- Os testes devem ser independentes — sem estado mutável partilhado entre testes.
- Os nomes dos testes devem descrever o cenário, não apenas o nome do método.

**Comentários**
- Escreve código auto-documentado primeiro; adiciona comentários apenas quando o *porquê* não for óbvio.
- Todas as classes e métodos públicos devem ter um comentário de documentação (docstring, `///`, Javadoc, etc.).

**Dependências**
- Mantém as dependências externas ao mínimo.
- Não adiciones uma dependência para algo que pode ser feito com a biblioteca padrão.
- Qualquer nova dependência deve ser discutida no PR.

---

## Mensagens de Commit

Este projecto segue a especificação **Conventional Commits**.

```
<tipo>(<âmbito>): <resumo curto>

[corpo opcional]
[rodapé(s) opcional/is]
```

**Tipos**

| Tipo       | Quando usar                                          |
|------------|------------------------------------------------------|
| `feat`     | Nova funcionalidade ou método RPC                    |
| `fix`      | Correcção de um problema                             |
| `docs`     | Apenas alterações de documentação                    |
| `test`     | Adicionar ou corrigir testes                         |
| `refactor` | Alteração de código que não é correcção nem feature  |
| `chore`    | Processo de build, actualizações de dependências     |

**Âmbitos:** `python`, `rust`, `typescript`, `java`, `<nova-linguagem>`, `docs`, 

**Exemplos**

```
feat(go): adicionar implementação inicial do cliente Go
feat(rust): adicionar método RPC getmempoolinfo
fix(python): tratar timeout de ligação correctamente
test(java): adicionar testes de integração regtest para carteira
docs(typescript): adicionar exemplo do sendrawtransaction
chore(deps): actualizar  para 0.27
```

> ⚠️ Commits que não sigam esta convenção serão pedidos para corrigir antes do merge.

---

## Processo de Pull Request

1. Faz fork do repositório e cria um branch a partir de `main`:
   ```bash
   git checkout -b feat/<linguagem>-implementacao-inicial
   # ou
   git checkout -b fix/<linguagem>-timeout-de-ligacao
   ```

2. Faz as tuas alterações seguindo os [Padrões de Código Limpo](#padrões-de-código-limpo).

3. Garante que todos os testes passam localmente: se tiver testes unitarios

4. Actualiza o `CHANGELOG.md` na secção `[Não Lançado]`.

5. Abre o PR contra `main` e preenche o template.

6. É necessária pelo menos **uma aprovação de um maintainer** antes do merge.

7. Os commits serão agrupados em squash no merge se o histórico estiver muito ruidoso.

---

## Reportar Problemas

Abre uma `issue de reporte de problema` e inclui:

- Versão do Bitcoin Core e rede (`testnet` / `regtest`)
- Linguagem e versão da biblioteca
- Exemplo mínimo que reproduz o problema
- Comportamento esperado vs comportamento real
- Logs ou mensagens de erro relevantes

---

Obrigado por ajudares a tornar o **bitcoin-rpc-clients-bitdevs-maputo** melhor! 