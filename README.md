# 📘 Guia Completo de Git — Passo a Passo Comentado e Estruturado

Este repositório é um manual prático e didático com as principais operações do Git.\
Desde a criação de um repositório até comandos avançados com *tags*, *branches*, conflitos e arquivos grandes.

---

## 🧼 1. Remover repositório Git existente (opcional)

Se o projeto já possui um `.git` e você quer reiniciar o histórico (ex: para conectar a outro repositório):

```bash
# PowerShell
rm -r -fo .git

# Ou no CMD
rmdir /s /q .git
```

> Isso **desvincula completamente** seu projeto do repositório Git atual.

---

## 🌐 2. Criar repositório remoto e copiar URL

1. Acesse [GitHub](w), [GitLab](w) ou [Bitbucket](w)
2. Clique em **Novo repositório**
3. Defina nome, descrição, visibilidade
4. NÃO adicione README (se for começar localmente)
5. Copie a URL HTTPS ou SSH

**Exemplo:**
```
https://github.com/usuario/repositorio.git
```

---

## 🍫 3. Instalar Chocolatey (opcional) e Git LFS (para arquivos grandes)

### ✅ Instalar Chocolatey (Windows)
```powershell
Set-ExecutionPolicy Bypass -Scope Process -Force; `
[System.Net.ServicePointManager]::SecurityProtocol = `
[System.Net.ServicePointManager]::SecurityProtocol -bor 3072; `
iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
```

### ✅ Instalar Git LFS
```bash
choco install git-lfs
```
ou baixe em: [https://git-lfs.github.com](https://git-lfs.github.com)

### ✅ Inicializar LFS
```bash
git lfs install
```

---

## 📄 4. Gerar `.gitignore` padrão

Evita subir arquivos desnecessários ou sensíveis.

**Exemplo básico para Node.js:**
```
node_modules/
dist/
.env
*.log
.vscode/
.DS_Store
```

Use [https://gitignore.io](https://gitignore.io) para gerar conforme sua linguagem.

---

## 🚀 5. Inicializar repositório local e conectar ao remoto

```bash
git init                             # Inicializa repositório local
git remote add origin <URL>         # Conecta ao repositório remoto
```

---

## 📦 6. Adicionar arquivos grandes ao Git LFS

```bash
git lfs track "*.extensao"          # Ex: git lfs track "*.onnx"
git add .gitattributes
git add caminho/do/arquivo
git commit -m "Adiciona arquivo com LFS"
```

---

## 📤 7. Subir arquivos e histórico inicial

```bash
git add .
git commit -m "Commit inicial do projeto"
git push -u origin main
```

---

## 🔄 8. Fazer `pull` e resolver conflitos (se houver)

```bash
git pull origin main --allow-unrelated-histories
```

Se houver conflitos:

- Busque trechos com `<<<<<<<`, `=======`, `>>>>>>>`
- Resolva manualmente
- Após resolver:
```bash
git add .
git commit -m "Resolve conflitos"
```

---

## 📂 9. Adicionar e remover arquivos

```bash
git add .                               # Adiciona tudo
git add pasta/arquivo.ext               # Adiciona específico
git reset pasta/arquivo.ext            # Remove do stage
git rm caminho/arquivo.ext             # Remove do disco e do Git
git commit -m "Remove arquivo"
```

---

## 💬 10. Commits e como desfazer

```bash
git commit -m "Mensagem clara"
```

### Desfazer último commit mantendo alterações:
```bash
git reset --soft HEAD~1
```

### Desfazer commit e alterações locais:
```bash
git reset --hard HEAD~1
```

---

## 🔖 11. Trabalhar com Tags

### Criar tag anotada:
```bash
git tag -a v1.0.0 -m "Versão 1.0.0"
```

### Apagar tag local:
```bash
git tag -d v1.0.0
```

### Apagar tag remota:
```bash
git push origin --delete tag v1.0.0
```

### Enviar tag:
```bash
git push origin v1.0.0
```

---

## 🔗 12. Alterar repositório remoto

```bash
git remote -v                         # Verificar remotes
git remote set-url origin <nova-url> # Atualizar origin
```

---

## 🔄 13. Baixar atualizações do repositório remoto

```bash
git pull origin main                      # Atualiza branch main
git fetch origin tag v1.0.0              # Busca tag específica
git checkout tags/v1.0.0                 # Alterna para tag
```

---

## 🚢 14. Enviar mudanças

```bash
git push origin main
```

---

## 🗑️ 15. Deletar tag local e remota

```bash
git tag -d v1.0.0
git push origin --delete tag v1.0.0
```

---

## 🧹 16. Deletar branch `main`

```bash
git branch -D main                  # Local
git push origin --delete main      # Remoto ⚠️ Atenção!
```

---

## 🛠️ 17. Substituir commit ou tag (forçar)

```bash
git tag -f v1.0.0
git push origin -f v1.0.0

git push origin main --force       # ⚠️ Só se tiver certeza
```

---

## 🌿 18. Criar e subir outra branch (ex: `master`)

```bash
git checkout -b master
git add .
git commit -m "Commit inicial na branch master"
git push origin master
```

---

## 🧩 19. Resolver conflitos

```bash
git status                          # Ver arquivos em conflito
git merge --abort                   # Cancelar merge
git add caminho/arquivo.ext         # Marcar como resolvido
git commit -m "Resolve conflitos"   # Finalizar
git checkout -- caminho/arquivo.ext # Descartar alterações
```

---

## 💡 Dicas extras

- ✍️ Sempre escreva mensagens claras de commit.
- 🌳 Use branches para novas funcionalidades.
- ⚠️ Evite `git push --force` em branches compartilhadas.
- 💾 Use Git LFS para arquivos grandes.
- 🔁 Faça `git pull` antes de subir mudanças.
- 🧘‍♂️ Resolva conflitos com calma e atenção.

---

## 🧪 Exemplos Completos — Primeira Vez vs Já Existe

---

### 🚀 Subir para a branch `main`

#### ✅ Primeira vez
```bash
git init                                      # Inicializa o repositório Git local
git remote add origin <url>                   # Conecta ao repositório remoto
git checkout -b main                          # Cria e entra na branch 'main'
git add .                                     # Adiciona todos os arquivos
git commit -m "Commit inicial na branch main" # Cria o commit
git push -u origin main                       # Envia branch e configura tracking remoto
```

#### 🔁 Já existe
```bash
git checkout main                             # Garante que está na branch main
git fetch origin                              # Baixa alterações do repositório remoto sem aplicar
git diff origin/main                          # Compara o que mudou entre sua branch atual e a versão remota
git pull origin main                          # Atualiza com possíveis mudanças do remoto
git add .                                     # Adiciona alterações feitas
git commit -m "Atualização de conteúdo"       # Cria novo commit
git push origin main                          # Envia mudanças ao remoto
```

---

### 🚀 Subir para a branch `release`

#### ✅ Primeira vez
```bash
git checkout -b release                       # Cria a branch 'release'
git add .
git commit -m "Criação da branch release"
git push -u origin release                    # Envia a branch e configura o tracking
```

#### 🔁 Já existe
```bash
git checkout release                          # Vai para a branch release
git pull origin release                       # Atualiza com possíveis alterações do remoto
git add .
git commit -m "Atualização na release"
git push origin release                       # Envia mudanças
```

---

### 🏷️ Subir uma tag `v1.0.0`

#### ✅ Primeira vez
```bash
git tag -a v1.0.0 -m "Versão 1.0.0 inicial"   # Cria a tag local com mensagem
git push origin v1.0.0                        # Envia a tag para o remoto
```

#### 🔁 Já existe
```bash
git tag -f v1.0.0                             # Atualiza tag local para novo commit
git push origin -f v1.0.0                     # Força atualização da tag remota
```

---

### 📥 Baixar da branch `main`

#### ✅ Primeira vez
```bash
git fetch origin                              # Busca todas as referências remotas
git checkout -b main origin/main              # Cria a branch main local e aponta para a remota
```

#### 🔁 Já existe
```bash
git checkout main                             # Troca para a branch
git pull origin main                          # Baixa e mescla atualizações
```

---

### 📥 Baixar da branch `release`

#### ✅ Primeira vez
```bash
git fetch origin                              # Atualiza referências remotas
git checkout -b release origin/release        # Cria a branch release local a partir da remota
```

#### 🔁 Já existe
```bash
git checkout release                          # Troca para a branch
git pull origin release                       # Atualiza com as mudanças
```

---

### 📥 Baixar uma tag `v1.0.0`

#### ✅ Primeira vez
```bash
git fetch origin tag v1.0.0                   # Baixa a tag do repositório remoto
git checkout tags/v1.0.0                      # Troca para o estado da tag
```

> ⚠️ Para editar a partir da tag:
```bash
git checkout -b nova-branch tags/v1.0.0
```

#### 🔁 Já existe
```bash
git fetch --tags                              # Atualiza todas as tags remotas
git checkout tags/v1.0.0                      # Vai para a tag desejada
```

---

## ❓ Preciso fazer `git pull` antes de `git push`?

### ✅ Você **pode** fazer `push` sem `pull`:
- Se a branch local e remota estão sincronizadas
- Se for a primeira vez enviando
- Se a branch/tag ainda não existe no remoto

### ⚠️ Você **deve fazer `pull` antes de `push`**:
- Se outro colaborador fez `push` antes de você
- Se o repositório remoto está à frente do seu local

### 🚫 Se tentar fazer `push` sem `pull`, e os históricos forem diferentes:
```text
! [rejected] main -> main (fetch first)
error: failed to push some refs to 'https://...'
```

### 💡 Solução perigosa (usa com atenção):
```bash
git push --force
```

> Isso sobrescreve o remoto. Use **apenas se tiver certeza** que não vai apagar o trabalho de outras pessoas.

---

Se este conteúdo foi útil, ⭐ favorite, compartilhe ou personalize!  
Feito com 💙 por quem ama Git e produtividade.

---

## 🤝 Contribuição

Sinta-se à vontade para sugerir melhorias, correções ou adicionar novos exemplos!  
Você pode contribuir de duas formas:

1. **Fork do repositório**
2. **Pull Request com suas alterações**

Toda contribuição é muito bem-vinda! 🚀

---

## 📬 Contato

Se você tiver dúvidas, sugestões ou quiser trocar ideia sobre Git, DevOps ou desenvolvimento em geral:

- GitHub: [@brunojfnet](https://github.com/brunojfnet)
- LinkedIn: [Bruno Rafael](https://www.linkedin.com/in/brunojfnet)

---

Feito com 💙 por [Bruno Rafael](https://github.com/brunojfnet) — Desenvolvedor Backend & Consultor de TI no Brasil 🇧🇷
