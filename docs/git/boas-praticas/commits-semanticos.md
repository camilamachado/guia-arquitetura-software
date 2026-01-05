# Commits Semânticos

Commits semânticos seguem um padrão de escrita que torna o histórico **mais legível, previsível e automatizável**, facilitando revisão de código, geração de changelogs e entendimento da evolução do projeto.

## 📘 Visão Geral

Um commit semântico descreve **o tipo da mudança**, **o contexto** e **o impacto**, usando uma mensagem curta, padronizada e objetiva.

Formato mais comum (_Conventional Commits_):

```text
<tipo>(<escopo>): <descrição>
```

Exemplo:

```text
✨ feat(auth): adicionar login com JWT
```

## 🧱 Estrutura do Commit

### 1️⃣ Tipo (obrigatório)

Indica a **natureza da mudança**.

| Tipo       | Emoji | Quando usar                                       |
| ---------- | ----- | ------------------------------------------------- |
| `feat`     | ✨    | Nova funcionalidade                               |
| `fix`      | 🐛    | Correção de bug                                   |
| `docs`     | 📝    | Alterações em documentação                        |
| `style`    | 🎨    | Formatação, lint, espaços (sem impacto funcional) |
| `refactor` | ♻️    | Refatoração sem alterar comportamento             |
| `test`     | 🧪    | Adição ou ajuste de testes                        |
| `chore`    | 🔧    | Tarefas de manutenção                             |
| `perf`     | ⚡    | Melhoria de performance                           |
| `ci`       | 🤖    | Alterações em pipelines / CI                      |
| `build`    | 📦    | Alterações no processo de build                   |

📌 **Observação:** o uso de emoji é opcional, mas recomendado para facilitar a leitura do histórico.

### 2️⃣ Escopo (opcional, recomendado)

Define **onde** a mudança ocorreu.

Exemplos:

```text
🐛 fix(api): corrigir erro 500 ao criar usuário
♻️ refactor(auth): simplificar validação de token
```

### 3️⃣ Descrição (obrigatória)

Regras para a descrição:

- Verbo no **imperativo (infinitivo)**
- Frase curta e objetiva
- Sem ponto final
- Primeira letra minúscula

❌ Incorreto:

```text
feat: adiciona nova tela
```

✅ Correto:

```text
feat: adicionar nova tela
```

## 🚀 Exemplos Práticos

```text
✨ feat(user): permitir atualização de perfil
```

```text
🐛 fix(order): corrigir cálculo de frete
```

```text
📚 docs(readme): adicionar instruções de setup
```

```text
♻️ refactor(auth): remover lógica duplicada
```

```text
🔧 chore(deps): atualizar versão do .NET SDK
```

## 💥 Commits com Breaking Changes

Quando a mudança **quebra compatibilidade**, indique explicitamente.

### Opção 1: `!` no tipo

```text
✨ feat(api)!: alterar contrato de criação de usuário
```

### Opção 2: Rodapé do commit

```text
✨ feat(api): alterar contrato de criação de usuário

BREAKING CHANGE: o campo "email" agora é obrigatório
```

## 🤖 Benefícios Práticos

- Histórico legível e padronizado
- Revisões de PR mais rápidas
- Geração automática de changelog
- Suporte a Versionamento Semântico (SemVer)
- Melhor comunicação entre times

## ⚠️ Pontos de Atenção

- Um commit deve representar **uma única intenção**
- Evite commits grandes e genéricos
- Padronização só funciona se todo o time seguir
- Combine commits semânticos com [**squash**](../comandos/git-squash.md) quando necessário

## ✅ Checklist antes de commitar

- [ ] Usei verbo no infinitivo?
- [ ] O tipo reflete a mudança?
- [ ] O escopo está claro?
- [ ] Esse commit faz apenas uma coisa?
