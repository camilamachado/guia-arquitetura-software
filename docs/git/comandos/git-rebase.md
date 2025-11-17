# Git Rebase

O `git rebase` permite reorganizar e atualizar o histórico de commits, mantendo uma linha do tempo mais limpa e linear.

## 📘 Visão Geral

O `git rebase` pega os commits da sua branch e “refaz” eles sobre outra branch — geralmente a `main` ou `develop`.
Diferente do _merge_, ele **reescreve o histórico**, criando uma linha do tempo mais limpa e linear, sem registros de merge commits.

Uma forma fácil de visualizar: imagine que sua branch é um caminho que você está construindo sobre uma estrada principal (`main`). O rebase **pega os blocos de construção da sua branch e os coloca novamente no topo da estrada principal**, como se você tivesse começado a construir sobre a versão mais recente da estrada.

## 🚀 Guia Prático

### Rebase simples (caso mais comum)

Atualizar sua branch com a `main`:

```bash
git fetch origin
git rebase origin/main
```

### Resolver conflitos durante o rebase

```bash
# Editar arquivos conflitantes
git add .
git rebase --continue
```

### Cancelar o rebase

```bash
git rebase --abort
```

### Atualizar PR após rebase

Depois do rebase, o histórico da sua branch é reescrito. Por isso, o push comum não funciona — você precisa forçar com segurança:

```bash
git push origin minha-branch --force-with-lease
```

### Quando fazer rebase em PRs?

| Situação                                  | Devo fazer rebase? | Por quê?                                         |
| ----------------------------------------- | ------------------ | ------------------------------------------------ |
| Antes de abrir o PR                       | ✅ Sim             | Limpa histórico e evita conflitos                |
| Depois de abrir o PR, se a main atualizar | ✅ Sim             | Mantém PR atualizado e fácil de revisar          |
| Antes de merge, sem conflitos             | ⚠️ Depende         | Merge normal: sim; squash/rebase automático: não |
| Branch compartilhada                      | ❌ Não             | Evita quebrar o histórico dos outros             |

## 🆚 Rebase vs Merge

| Aspecto   | Merge                         | Rebase                     |
| --------- | ----------------------------- | -------------------------- |
| Histórico | Mantém histórico com _merges_ | Histórico linear           |
| Segurança | Fácil e seguro                | Reescreve commits          |
| Uso ideal | Branches de longa duração     | PRs limpos e organizados   |
| Commits   | Não altera SHA                | Altera SHA dos commits     |
| Conflitos | Ocorrem apenas uma vez        | Podem ocorrer várias vezes |

## ⚠️ Pontos de Atenção

- Rebase **reescreve o histórico**, use com cuidado.
- Conflitos podem surgir várias vezes.
