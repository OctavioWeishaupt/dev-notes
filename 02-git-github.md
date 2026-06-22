# 02 — Git e GitHub

📚 **Cursos:** Git e GitHub — Alura (2 cursos) · GitHub Skills (7 labs) · Learn Git Branching  
🔗 **Fontes:** alura.com.br · skills.github.com · learngitbranching.js.org  
✅ **Status:** Concluído  
📅 **Período:** Junho/2026

---

## O que é Git e o que é GitHub

- **Git** — sistema de controle de versão local. Rastreia o histórico de alterações do projeto na sua máquina.
- **GitHub** — plataforma remota que hospeda repositórios Git. Permite colaboração, backup e portfólio.
- Git funciona sem GitHub. GitHub não funciona sem Git.

---

## Configuração inicial

```bash
git config --global user.name "Seu Nome"
git config --global user.email "seu@email.com"
```

---

## Criar e linkar repositório

```bash
# Iniciar repo local do zero
git init

# Clonar repo existente do GitHub
git clone URL_DO_REPO

# Linkar repo local a um remoto
git remote add origin URL_DO_REPO
git branch -M main
git push -u origin main
```

---

## Fluxo de trabalho diário

```bash
git status                    # ver o que mudou
git add .                     # preparar todas as mudanças
git add arquivo.js            # preparar arquivo específico
git commit -m "feat: descrição"  # commitar com mensagem semântica
git push origin main          # enviar para o GitHub
git pull origin main          # puxar atualizações do remoto
```

### Tipos de commit semântico
| Prefixo | Uso |
|---|---|
| `feat:` | nova funcionalidade |
| `fix:` | correção de bug |
| `docs:` | documentação |
| `refactor:` | melhoria sem mudar comportamento |
| `chore:` | tarefas de manutenção |

---

## Branches

```bash
git branch                    # listar branches
git branch nome-da-branch     # criar branch
git checkout nome-da-branch   # trocar para branch
git checkout -b nome-da-branch  # criar e já trocar
git switch nome-da-branch     # alternativa moderna ao checkout
git merge nome-da-branch      # mesclar branch na atual
git branch -d nome-da-branch  # deletar branch local
```

---

## Fluxo de trabalho em equipe (sprint)

Quando estás na sua branch e a main remota foi atualizada:

```bash
git fetch origin              # baixa atualizações sem aplicar
git merge origin/main         # traz mudanças da main para sua branch
# resolve conflitos se houver
git push origin sua-branch    # envia sua branch atualizada
```

**merge vs rebase:**
- `git merge origin/main` — mais seguro, preserva histórico real. Preferência em branches compartilhadas.
- `git rebase origin/main` — histórico mais limpo, reescreve commits. Melhor para branches pessoais antes do PR.

**Quando não resolver conflito sozinho:** quando o conflito é em arquivo que você não entende o contexto das mudanças do colega. Fala com quem atualizou antes de resolver às cegas.

---

## Pull Requests

Fluxo padrão:
1. Cria sua branch → faz commits → push para o GitHub
2. No GitHub: abre Pull Request da sua branch para a main
3. Time revisa, comenta, aprova
4. Merge feito (por você ou pelo time)

---

## Merge Conflicts

Acontece quando duas pessoas editam o mesmo trecho do mesmo arquivo. Git marca assim:

```
<<<<<<< HEAD
  seu código
=======
  código da outra branch
>>>>>>> outra-branch
```

Resolve manualmente, salva o arquivo, depois:

```bash
git add arquivo-resolvido.js
git commit -m "fix: resolve merge conflict"
```

---

## Git Stash

Salva mudanças temporariamente sem commitar — útil quando precisa trocar de branch mas não quer fazer commit ainda.

```bash
git stash            # guarda as mudanças
git stash pop        # recupera as mudanças guardadas
git stash list       # lista os stashes salvos
```

---

## Comandos avançados — consulta quando precisar

| Comando | O que faz |
|---|---|
| `git fetch origin` | Baixa atualizações sem aplicar |
| `git log --oneline` | Histórico de commits resumido |
| `git diff` | Ver diferenças antes de commitar |
| `git reset HEAD~1` | Desfaz o último commit (mantém arquivos) |
| `git cherry-pick HASH` | Aplica um commit específico de outra branch |
| `git rebase main` | Reaplica seus commits em cima da main |
| `git pull --rebase` | Pull que usa rebase ao invés de merge |

> ⚠️ Cherry-pick, rebase e reset são poderosos e fáceis de errar. Sempre consultar antes de usar em situação de dúvida.

---

## Conceito central

> Git é sobre intenção, não sobre decorar comandos.  
> Saber o que você quer fazer (salvar, enviar, buscar, mesclar) é mais importante que lembrar a sintaxe exata — essa você consulta.

---

## O que ainda consolida só com prática

- Intuição para escolher entre merge e rebase
- Resolver conflitos com confiança
- Entender o que o git log está te mostrando
- Usar cherry-pick e reset com segurança
