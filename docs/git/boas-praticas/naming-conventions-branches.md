# Naming Conventions para Branches

Definir um padrão de nomenclatura para branches ajuda a manter o repositório **organizado, legível e previsível**, facilitando a colaboração entre pessoas e a automação de processos (CI/CD, releases, reviews).

## 📘 Visão Geral

Uma branch bem nomeada deve responder rapidamente:

- **O que está sendo feito?**
- **Por que essa branch existe?**
- **Qual o contexto da mudança?**

Um bom nome evita ambiguidades, reduz erros no fluxo de trabalho e melhora a rastreabilidade das mudanças.

Formato recomendado:

```text
<tipo>/<descricao-curta>
```

Exemplo:

```text
feature/login-com-jwt
```

## 🧱 Estrutura da Branch

### 1️⃣ Tipo (obrigatório)

Indica a **intenção da branch**.

| Tipo       | Quando usar                   |
| ---------- | ----------------------------- |
| `feature`  | Nova funcionalidade           |
| `fix`      | Correção de bug               |
| `hotfix`   | Correção crítica em produção  |
| `refactor` | Refatoração de código         |
| `chore`    | Tarefas técnicas / manutenção |
| `docs`     | Documentação                  |
| `test`     | Testes                        |
| `release`  | Preparação de release         |

### 2️⃣ Descrição (obrigatória)

Regras para a descrição:

- Letras minúsculas
- Separar palavras com `-`
- Curta e objetiva
- Sem caracteres especiais
- Sem espaços

✅ Correto:

```text
feature/cadastro-de-usuario
fix/corrigir-erro-login
docs/atualizar-readme
```

❌ Incorreto:

```text
Feature/CadastroUsuario
bugFix-login
ajustes
```

## 🚀 Exemplos Práticos

```text
feature/implementacao-pagamento-pix
fix/corrigir-calculo-frete
hotfix/erro-critico-autenticacao
refactor/remover-logica-duplicada
chore/atualizar-dependencias
docs/documentacao-git-squash
test/adicionar-testes-autenticacao
```

## 🔢 Uso de Identificador de Tarefa (opcional)

Quando integrado a ferramentas como Jira, Azure Boards ou GitHub Issues, recomenda-se incluir o ID da tarefa.

Formato:

```text
<tipo>/<id-da-tarefa>-<descricao>
```

Exemplo:

```text
feature/123-cadastro-usuario
fix/456-corrigir-timeout-api
```

## 🆚 Branches Bem Nomeadas vs Genéricas

| Genérica       | Padronizada                          |
| -------------- | ------------------------------------ |
| `teste`        | `test/validacao-login`               |
| `ajustes`      | `refactor/ajustar-servico-pagamento` |
| `nova-feature` | `feature/relatorio-financeiro`       |
| `bugfix`       | `fix/corrigir-erro-upload`           |

## ⚠️ Pontos de Atenção

- Evite nomes genéricos
- Não use nomes de pessoas
- Não reutilize branches antigas
- Mantenha o padrão em todo o time
- Delete branches após o merge

## ✅ Checklist antes de criar a branch

- [ ] O tipo representa corretamente a intenção?
- [ ] A descrição é clara e curta?
- [ ] O nome segue o padrão do time?
- [ ] A branch está associada a uma tarefa ou objetivo?
