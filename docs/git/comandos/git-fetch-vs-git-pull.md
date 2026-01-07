# Git Fetch vs Git Pull

Os comandos `git fetch` e `git pull` são usados para **atualizar informações do repositório remoto**, mas têm comportamentos diferentes e impactos distintos no seu código local.

Entender essa diferença é essencial para evitar conflitos inesperados e manter controle sobre o histórico.

## 📘 Visão Geral

### `git fetch`

O `git fetch` **baixa as atualizações do repositório remoto**, mas **não altera sua branch atual**.

Ele atualiza apenas as referências remotas (`origin/main`, `origin/develop`, etc.), permitindo que você **analise as mudanças antes de integrá-las**.

### `git pull`

O `git pull` é um atalho que executa dois passos:

```text
git fetch + git merge
```

Ou, dependendo da configuração do time:

```text
git fetch + git rebase
```

Ou seja, além de baixar as mudanças, ele **integra automaticamente** na sua branch atual.

## 🧠 Forma de Visualizar

- `git fetch` → **Ver o que mudou**
- `git pull` → **Ver e aplicar o que mudou**

## 🚀 Guia Prático

### Usando `git fetch`

Buscar atualizações do remoto:

```bash
git fetch origin
```

Ver diferenças antes de integrar:

```bash
git log HEAD..origin/main
```

Ou:

```bash
git diff main origin/main
```

Integrar manualmente (merge):

```bash
git merge origin/main
```

Ou (rebase):

```bash
git rebase origin/main
```

---

### Usando `git pull`

Atualizar e integrar automaticamente:

```bash
git pull origin main
```

Com rebase (recomendado em muitos times):

```bash
git pull --rebase origin main
```

## 🆚 Fetch vs Pull

| Aspecto                    | Fetch         | Pull           |
| -------------------------- | ------------- | -------------- |
| Baixa atualizações         | ✅ Sim        | ✅ Sim         |
| Atualiza branch local      | ❌ Não        | ✅ Sim         |
| Risco de conflito imediato | ❌ Não        | ✅ Sim         |
| Controle sobre integração  | Alto          | Baixo          |
| Recomendado para           | Times maduros | Fluxos simples |

## 🤝 Fluxo Recomendado (times que usam rebase)

```bash
git fetch origin
git rebase origin/main
```

Esse fluxo:

- Dá visibilidade total do que mudou
- Evita merges automáticos
- Mantém histórico linear

## ⚠️ Pontos de Atenção

- `git pull` pode criar **merge commits inesperados**
- Sempre saiba se seu `pull` está configurado para `merge` ou `rebase`
- Prefira `fetch` + ação explícita em times com padrão definido
- Leia conflitos com atenção antes de resolver
