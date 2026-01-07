# Git Stash

O `git stash` permite **salvar temporariamente mudanças não commitadas**, limpando o diretório de trabalho para que você possa trocar de branch ou executar outras tarefas sem perder progresso.

É ideal para situações em que você **precisa interromper o trabalho atual**, mas ainda não está pronto para criar um commit.

## 📘 Visão Geral

O stash funciona como uma **gaveta temporária** onde o Git guarda:

- Alterações em arquivos rastreados
- Alterações staged e unstaged (por padrão)

Após aplicar ou descartar o stash, o código volta ao estado anterior.

Uma forma simples de visualizar: imagine que você está no meio de uma tarefa e precisa atender algo urgente.  
O `git stash` **guarda tudo rapidamente**, permitindo voltar exatamente de onde parou depois.

## 🚀 Guia Prático

### Criar um stash

Salvar alterações atuais:

```bash
git stash
```

Ou com mensagem (recomendado):

```bash
git stash push -m "ajustes iniciais no fluxo de pagamento"
```

---

### Listar stashes

```bash
git stash list
```

Exemplo de saída:

```text
stash@{0}: On feature/pagamento: ajustes iniciais no fluxo de pagamento
stash@{1}: On develop: testes temporários
```

---

### Aplicar um stash

Aplicar o stash mais recente:

```bash
git stash apply
```

Aplicar um stash específico:

```bash
git stash apply stash@{1}
```

---

### Remover stashes

Remover um stash específico:

```bash
git stash drop stash@{0}
```

Remover todos os stashes:

```bash
git stash clear
```

## 🆚 Stash vs Commit Temporário

| Stash                       | Commit                 |
| --------------------------- | ---------------------- |
| Temporário                  | Permanente             |
| Não altera histórico        | Altera histórico       |
| Não precisa mensagem formal | Requer mensagem        |
| Ideal para interrupções     | Ideal para checkpoints |

## 🤝 Boas Práticas

- Use stash para **interrupções curtas**
- Sempre prefira `git stash push -m`
- Não acumule muitos stashes
- Limpe stashes antigos
- Evite stash por longos períodos

## ⚠️ Pontos de Atenção

- Stash **não substitui commit**
- Pode gerar conflitos ao aplicar
- Stashes não são compartilhados
- Stash também pode ser perdido se não gerenciado
