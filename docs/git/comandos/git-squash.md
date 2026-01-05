# Git Squash

O **git squash** é uma técnica usada para **combinar vários commits em um único commit**, deixando o histórico mais limpo, objetivo e fácil de entender.

Embora não exista um comando chamado `git squash`, essa operação pode ser realizada de diferentes formas, sendo a mais comum através do **rebase interativo** ou diretamente no merge de Pull Requests.

## 📘 Visão Geral

Durante o desenvolvimento, é comum criar commits pequenos, intermediários ou experimentais (`wip`, ajustes, correções incrementais).
O squash permite **agrupar esses commits relacionados em um commit final bem definido**, geralmente seguindo o padrão de **commits semânticos**.

Uma forma simples de visualizar: imagine que você fez vários rascunhos enquanto escrevia um texto.  
O squash é o processo de **juntar tudo em uma versão final bem escrita**, ocultando os rascunhos do histórico.

## 🚀 Guia Prático

### Squash no merge do Pull Request (forma mais fácil)

Plataformas como **GitHub, GitLab e Azure DevOps** oferecem a opção **Squash and merge**.

Nesse fluxo:

- Todos os commits do PR são combinados em um único commit
- Você define uma mensagem final de commit
- Não é necessário realizar squash localmente

---

### Squash usando rebase interativo (forma padrão do Git)

1. Atualize sua branch:

```bash
git fetch origin
```

2. Inicie o rebase interativo:

```bash
git rebase -i origin/main
```

3. O editor abrirá algo como:

```text
pick a1b2c3 wip
pick d4e5f6 ajuste de layout
pick g7h8i9 corrigir bug de validação
```

4. Altere para:

```text
pick a1b2c3 🐛 fix(auth): corrigir validação de token
squash d4e5f6
squash g7h8i9
```

5. Salve e edite a mensagem final do commit.

---

### Squash rápido com `fixup` e `autosquash`

Para pequenos ajustes em commits já existentes:

```bash
git commit --fixup <hash-do-commit>
git rebase -i --autosquash origin/main
```

O Git irá automaticamente agrupar os commits de correção no commit original.

---

### Atualizar o PR após squash

Como o histórico foi reescrito, é necessário forçar o push com segurança:

```bash
git push origin minha-branch --force-with-lease
```

---

## 📌 Quando usar squash?

| Situação                                 | Devo usar squash? | Por quê?                |
| ---------------------------------------- | ----------------- | ----------------------- |
| Muitos commits pequenos da mesma feature | ✅ Sim            | Remove ruído            |
| Commits de WIP, testes ou ajustes        | ✅ Sim            | Limpa histórico         |
| Correções incrementais do mesmo bug      | ✅ Sim            | Consolida intenção      |
| Commits já semânticos e bem separados    | ❌ Não            | Histórico já está claro |
| Branch compartilhada                     | ❌ Não            | Reescreve histórico     |

---

## 🆚 Squash vs Rebase vs Merge

| Aspecto             | Merge                     | Rebase            | Squash              |
| ------------------- | ------------------------- | ----------------- | ------------------- |
| Histórico           | Preserva todos os commits | Lineariza commits | Condensa commits    |
| Reescreve histórico | ❌ Não                    | ✅ Sim            | ✅ Sim              |
| Uso ideal           | Branches longas           | Atualizar PRs     | Finalizar PRs       |
| Granularidade       | Alta                      | Alta              | Baixa (intencional) |

---

## 🤝 Squash + Commits Semânticos

O squash funciona melhor quando o commit final segue um padrão semântico.

Antes:

```text
wip
ajuste
corrigir teste
bug fix
```

Depois:

```text
🐛 fix(order): corrigir cálculo de frete
```

## ⚠️ Pontos de Atenção

- Squash **reescreve o histórico**
- Nunca use squash em branches compartilhadas
- Após squash, sempre utilize `--force-with-lease`
- Revise cuidadosamente a mensagem final do commit
