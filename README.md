**💪 Guia Completo de Git no VS Code (Comentado)**

Este guia cobre do zero ao avançado para trabalhar com Git no VS Code, incluindo: iniciar o repositório, fazer commits, criar tags, trabalhar com branches e resolver conflitos.

**🔵 Iniciar um repositório Git no projeto**
````
git init                                # Inicia o controle de versão Git na pasta atual
````
**📂 Adicionar arquivos para commit**
````
git add nome_arquivo.ext                # Adiciona um arquivo específico
git add nome_da_pasta/                 # Adiciona uma pasta inteira
git add .                              # Adiciona todos os arquivos e pastas alterados (menos os ignorados)
````
**✅ Fazer commit com mensagem**
````
git commit -m "feat: primeira versão com estrutura básica"   # Faz commit com um comentário claro
````
**📆 Criar e enviar uma tag para versão**
````
git tag -a v1.0.0 -m "Primeira versão estável"  # Cria uma tag com comentário

git push origin v1.0.0                      # Envia essa tag para o GitHub
````
**⚠️ Tag não é uma branch. Ela é um marcador fixo em um commit específico.**

**☁️ Conectar ao GitHub e fazer push na branch principal (main)**
````
git remote add origin https://github.com/usuario/repositorio.git

# (se a branch não for main ainda)
git branch -M main                         # Define a branch principal como main
git push -u origin main                    # Envia os commits para o GitHub
````
**🔿 Ver status e mudanças antes de subir**
````
git status                                # Verifica arquivos alterados, não rastreados, staged

git diff                                  # Mostra alterações linha por linha
````
**⛔️ Remover commits (antes e depois do push)**

Localmente (sem push ainda):
````
git reset --soft HEAD~1                   # Remove o commit, mas mantém arquivos no stage
git reset --mixed HEAD~1                  # Remove o commit e o stage, mas mantém arquivos
````
Se já tiver feito push:
````
git reset --hard HEAD~1                   # Volta localmente

git push origin main --force              # Força a substituição do histórico remoto
````
⚠️ Use --force com cuidado. Isso sobrescreve o histórico no GitHub.

**🔀 Baixar do GitHub (sincronizar local com remoto)**
````
git pull origin main                      # Baixa e aplica atualizações da main do GitHub
````
Se houver conflitos, o VS Code mostra opções:
````
Aceitar alterações locais

Aceitar alterações remotas

Aceitar ambos
````
Após resolver:
````
git add arquivo
git commit -m "fix: resolvido conflito"
````
**🌱 Criar nova branch e fazer push**
````
git checkout -b feature/nome              # Cria e troca para nova branch
git add .
git commit -m "feat: implementa login"
git push -u origin feature/nome           # Sobe a branch nova para o GitHub
````
**📅 Criar nova tag e subir**
````
git tag -a v1.1.0 -m "Versão com login"
git push origin v1.1.0
````
**📂 Mudar para uma branch existente (remota ou local)**
````
git fetch                                 # Atualiza lista de branches e tags remotas
git checkout nome-da-branch               # Troca para a branch especificada
````
**📆 Mudar para uma tag (modo leitura)**
````
git fetch --tags

git checkout v1.0.0                       # Vai para o estado do código marcado pela tag
````
**📋 Unir uma branch com a main**
````
git checkout main

git pull origin main                      # Garante que a main está atualizada

git merge feature/nome                    # Junta a branch na main

git push origin main                      # Sobe a nova main para o GitHub
````
**📄 Diferença entre push main e push tag**
````
git push origin main envia o histórico atual da branch principal.

git push origin v1.0.0 envia um ponto congelado do projeto (snapshot).
````
A tag não é uma branch, ela aponta para um commit exato.

Se você seguir esse guia passo a passo, estará trabalhando com Git como um profissional. 🚀
