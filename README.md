# 📒Apostila de Introdução ao Git
## 1. Introdução ao Git
O Git é um sistema de controle de versões distribuído, amplamente utilizado no desenvolvimento de software para rastrear alterações no código ao longo do tempo. Ele permite que múltiplos desenvolvedores trabalhem colaborativamente em um projeto, mantendo um histórico de todas as modificações.

## 2. Criando um Repositório Local
Para começar a usar o Git em um projeto existente ou novo, você precisa inicializar um repositório Git.

Passos:

- Navegue até o diretório do seu projeto:

Bash
``` $ mkdir nomeDiretorio ```
``` $ cd nomeDiretorio ```

Inicialize o Git no diretório: Este comando cria um subdiretório .git oculto, que contém todos os metadados do seu repositório.

Bash

``` $ git init ```
Explore o diretório .git (opcional):

Bash

``` $ cd .git ```
Este diretório contém a estrutura interna do Git. Geralmente, você não precisa interagir diretamente com os arquivos dentro dele. Para voltar ao diretório principal:

Bash

``` $ cd .. ```
## 3. Clonando um Repositório Remoto
Para trabalhar em um projeto hospedado remotamente (como no GitHub, GitLab ou Bitbucket), você precisa clonar o repositório para sua máquina local.

Comando:

Bash

```$ git clone <URL_do_repositório> ```
Exemplo:

Bash

```$ git clone https://github.com/usuario/nome-do-repositorio.git ```
Observação sobre origin: Quando você clona um repositório remoto, o Git automaticamente cria um atalho chamado origin que aponta para a URL desse repositório remoto. Este é o nome padrão para o repositório remoto de onde você clonou.

Verificando os remotos:

Bash

``` $ git remote -v ```
Este comando exibe os nomes e URLs dos repositórios remotos configurados.

## 4. Conectando um Repositório Local a um Remoto
Se você já tem um repositório local e deseja conectá-lo a um repositório remoto (por exemplo, um repositório vazio que você criou no GitHub), siga estes passos:

Crie um repositório no serviço remoto (por exemplo, GitHub) e copie a URL.

Adicione o repositório remoto ao seu repositório local: O comando git remote add cria uma nova conexão com um repositório remoto. Por convenção, o primeiro remoto adicionado é chamado origin.

Bash

``` $ git remote add origin <URL_do_repositório_remoto> ```
## 5. Clonando uma Branch Específica
Por padrão, o comando git clone baixa todas as branches do repositório remoto. Se você deseja clonar apenas uma branch específica, use a opção ```--branch e --single-branch ```.

Comando:

Bash

``` $ git clone <URL_do_repositório> --branch <nome_da_branch> --single-branch ```

Exemplo:

Bash

``` $ git clone https://github.com/usuario/nome-do-repositorio.git --branch feature-1 --single-branch ```

## 6. Salvando Suas Alterações (Committing)
O Git rastreia as alterações feitas nos seus arquivos. Para salvar essas alterações no histórico do repositório, você precisa realizar um "commit".

Passos:

-Verifique o status do seu repositório: Este comando mostra quais arquivos foram modificados, adicionados ou removidos e se estão prontos para serem commitados.

Bash

``` $ git status ``` 
-Adicione os arquivos modificados à área de preparação (staging area): Antes de commitar, você precisa informar ao Git quais alterações você deseja incluir no próximo commit.

Para adicionar um arquivo específico:
Bash

``` $ git add <nome_do_arquivo> ```
Para adicionar todos os arquivos modificados e não rastreados:
Bash

```$ git add .```
-Comete as alterações: Este comando salva as alterações preparadas no histórico local do repositório. É importante escrever uma mensagem de commit clara e concisa, descrevendo as mudanças feitas.

Bash

```$ git commit -m "Mensagem descritiva do commit"```
Visualize o histórico de commits:

Bash

```$ git log```
Este comando exibe uma lista de commits, mostrando informações como o autor, a data e a mensagem de cada commit.

## 7. Ignorando Arquivos
Muitas vezes, existem arquivos que você não deseja que o Git rastreie (por exemplo, arquivos temporários, arquivos de configuração específicos do seu ambiente, etc.). Para ignorar esses arquivos, você pode criar um arquivo chamado .gitignore na raiz do seu repositório e listar os padrões de nomes de arquivos ou diretórios que devem ser ignorados.

Exemplo de um arquivo .gitignore:

``` *.log node_modules/ .env ```

Mantendo diretórios vazios: O Git não rastreia diretórios vazios. Se você precisa que um diretório vazio seja incluído no repositório (por exemplo, para que a estrutura de pastas seja mantida), a convenção é criar um arquivo vazio chamado ```.gitkeep``` dentro desse diretório.

## 8. Desfazendo Alterações Locais
Desfazendo o git init: Para desfazer a inicialização do Git em um diretório, basta excluir a pasta ```.git```. Cuidado: Isso removerá todo o histórico do Git naquele diretório.

Desfazendo alterações em arquivos não commitados: O comando git restore é usado para desfazer alterações em arquivos.

Para descartar alterações na área de trabalho (arquivos modificados, mas não adicionados ao staging):
Bash

```$ git restore <nome_do_arquivo>```

Para remover arquivos da área de preparação (staging area), mantendo as alterações no diretório de trabalho:
Bash

```$ git restore --staged <nome_do_arquivo>``` 

Alterando a mensagem do último commit: Se você cometeu um erro na mensagem do último commit, pode corrigi-la com o seguinte comando:

Bash

```$ git commit --amend -m "Nova mensagem"```

Cuidado: Não use --amend em commits que já foram enviados para um repositório remoto compartilhado, pois isso pode causar problemas para outros colaboradores.

## 9. Desfazendo Commits
O Git oferece diferentes maneiras de desfazer commits, dependendo do que você deseja alcançar.

``` git reset --soft <hash_do_commit>```: Desfaz o commit, mas mantém as alterações na área de preparação. Isso permite que você modifique o commit ou crie um novo commit com as alterações.

```git reset --mixed <hash_do_commit>```: Desfaz o commit e remove as alterações da área de preparação, mas mantém as alterações no seu diretório de trabalho. Este é o modo padrão do git reset.

```git reset --hard <hash_do_commit>```: Desfaz o commit e descarta todas as alterações no seu diretório de trabalho. Use este comando com extrema cautela, pois as alterações descartadas são perdidas permanentemente.

Para encontrar o hash de um commit, use o comando git log.

## 10. Histórico Detalhado com git reflog
O comando git reflog fornece um histórico mais detalhado das ações realizadas no seu repositório local, incluindo mudanças de branch, resets e commits. É uma ferramenta útil para recuperar commits perdidos ou entender o histórico do seu repositório.

Bash

```$ git reflog```

## 11. Interagindo com Repositórios Remotos
Para colaborar com outros desenvolvedores, você precisará enviar ```(push)``` suas alterações locais para um repositório remoto e baixar ```(pull)``` as alterações feitas por outros.

Adicionando um remoto (se ainda não foi feito):

Bash

```$ git remote add origin <URL_do_repositório_remoto>```

Renomeando a branch principal: Por convenção, a branch principal de um repositório agora é frequentemente chamada de main em vez de master. Se o seu repositório remoto foi criado com a branch principal chamada main, você pode renomear sua branch local correspondente:

Bash

```$ git branch -M main```

Enviando commits para o remoto: O comando git push envia seus commits locais para um repositório remoto. A opção -u (ou --set-upstream) associa sua branch local à branch remota correspondente pela primeira vez, para que você possa usar git push e git pull no futuro sem especificar o remoto e a branch.

Bash

```$ git push -u origin main```

Atalho para edição web no GitHub: No GitHub, enquanto visualiza arquivos em um repositório, pressionar a tecla . (ponto) abre um editor web baseado no VS Code, permitindo edições rápidas diretamente no navegador.

Atualizando seu repositório local: O comando git pull baixa as alterações do repositório remoto e as mescla com sua branch local atual.

Bash

```$ git pull origin main```

## 12. Trabalhando com Branches
Branches permitem que você trabalhe em diferentes funcionalidades ou correções de bugs isoladamente, sem afetar a branch principal (geralmente main).

Criando uma nova branch:

Bash

```$ git checkout -b <nome_da_nova_branch>```
Este comando cria uma nova branch com o nome especificado e muda para ela (checkout).

Voltando para a branch principal:

Bash

```$ git checkout main```
Listando branches:

- Para exibir todas as branches locais:
Bash

```$ git branch```
Para exibir as últimas informações de commit de cada branch local:
Bash

```$ git branch -v```
Mesclando branches (merge): Para integrar as alterações de uma branch (por exemplo, teste) na branch atual (por exemplo, main), use o comando git merge:

Bash

```$ git checkout main```
```$ git merge teste```
- Excluindo uma branch local:

Bash

```$ git branch -d teste```
Use ```-D``` em vez de ```-d``` para forçar a exclusão de uma branch que não foi totalmente mesclada.

## 13. Conflitos de Merge
Conflitos de merge ocorrem quando você mescla branches que têm alterações conflitantes na mesma linha de código em um mesmo arquivo. O Git não consegue decidir automaticamente qual alteração manter e marca o arquivo com marcadores de conflito (<<<<<<<, =======, >>>>>>>). 
Você precisará editar manualmente o arquivo para resolver o conflito, escolher qual alteração manter e remover os marcadores de conflito. Após resolver os conflitos, adicione o arquivo modificado ao staging (```git add```) e crie um novo commit para concluir a mesclagem.

## 14. Comandos Úteis no Dia a Dia
git fetch origin main: Baixa as alterações da branch main do repositório remoto origin, mas não as mescla com sua branch local. Isso permite que você veja as alterações remotas antes de integrá-las.

```git diff```: Exibe as diferenças entre diferentes estados do seu repositório.

```git diff```: Mostra as alterações entre sua área de trabalho e a área de preparação.
```git diff --staged```: Mostra as alterações entre a área de preparação e o último commit.
```git diff <branch>```: Mostra as diferenças entre sua branch atual e a branch especificada.
```git merge origin/main```: Após um ```git fetch```, este comando mescla as alterações baixadas da branch main do remoto origin para sua branch local atual.

## 15. Clonando uma Branch Específica (Repetição)
(Já abordado na seção 5)

Bash

```$ git clone <URL_do_repositório> --branch <nome_da_branch> --single-branch```

## 16. Arquivando Modificações com git stash
O comando git stash permite salvar temporariamente suas alterações não commitadas para que você possa trabalhar em outra coisa e depois voltar para suas alterações salvas.

Arquivando as alterações:

Bash

```$ git stash```

- Listando os stashes:

Bash

```$ git stash list```

- Aplicando o stash mais recente e removendo-o da lista:

Bash

```$ git stash pop```

- Aplicando um stash específico (sem removê-lo da lista):

Bash

``` $ git stash apply stash@{<número>}```
O número do stash pode ser encontrado com git stash list.

## 17 - Documentação
[Git Documentation](https://git-scm.com/doc)

