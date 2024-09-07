# Bem vindo ao manual de contribuição!

Nesse arquivo você irá encontrar uma base para entender como você pode interagir e contribuir com o repositório!

Todos os passos desse repositório pressupõe que você já tenha o git instalado e configurado na sua máquina, caso não possua, siga o manual de instalação e configuração!

[Instalando o git](https://git-scm.com/book/pt-br/v2/Come%C3%A7ando-Instalando-o-Git)

## Primeira Interação
Na primeira vez que for interagir com o repositório é interessante que você organize o local onde irá realizar o seu `git clone`. Uma indicação é que você siga um caminho como `Documentos/Faculdade` e dentro dessa pasta/diretṕrio você realiza o clone do repositório.

Depois de definir exatamente onde você irá trabalhar com o projeto, execute no terminal o comando `git init`

### Clone
O processo de clone é muito tranquilo, as duas opções principais são por HTTP ou SSH, recomendo que invistam um pouco do seu tempo e configurem uma chave SSH para interagir com o projeto e também com outros, pois ela permite fazer commits assinados e também evitam o problema de autenticação por meio de token de acesso no repositório.

[Manual para chave SSH](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)

Após configurar sua chave SSH ou até mesmo escolher o protocolo HTTP, basta rodar o seguinte comando

#### HTTP

```shell
git clone https://github.com/juanzeen/UENF1-POO.git
```

#### SSH

```shell
git clone git@github.com:seu_user/UENF1-POO.git
```

Esse comando irá criar uma nova pasta dentro do diretório onde você realizou o clone, para acessar essa pasta que possui o git inicializado, basta executar `cd UENF1-POO`.

## Interagindo com o repositório
Depois de ter o repositório criado em sua máquina, você seguirá alguns passos para que posteriormente as suas alterações possam ser aceitas e colocadas no repositório online.

### Lidando com branches

A primeira coisa que faremos é definir que a branch criada automaicamente é a branch main, rodando o seguinte comando:

```
git branch -M main
```
- Este comando simplesmente muda o nome da branch atual em que estamos.

Contudo, não trabalheremos na main, pois isso é contra as boas práticas e possui alta chance de prejudicar o projeto, já que a main deve sempre ser a branch final da aplicação, com todas as features testadas e aprovadas pelos participantes do projeto.

#### Saindo da branch main e criando uma nova branch de trabalho
Para sair da branch e criar uma branch para realizar alterações no projeto execute este comando:

```
git checkout -b nome_da_branch
```

O nome da branch normalmente é colocado pensando em deixar o mais claro possível o conteúdo colocado dentro dela, seguindo algumas convenções e prefixos.

O comando `checkout` serve para que consigamos navegar entre as branches que existem em nossa máquina, contudo, usando o opcional `-b` criamos uma nova branch e em seguida movemos pra ela. Caso precisemos voltar a main depois, basta fazer um `git checkout main`, _sem utilizar o -b_.

Ideias de nome para branches:
- feat-novo-recurso -> usamos esse modelo de nome para quando criamos uma nova feature no projeto, um exemplo seria: feat-pagina-de-corredores;
- fix-consertando-erro -> modelo usado para quando a branch foi criada com o intuito de consertar algo, um exemplo seria: fix-consertando-formato-fotos;
- delete-arquivo-apagado -> modelo usado para especificar um arquivo ou feature apagada, pois parou de ter utilidade para o projeto, exemplo: delete-enviar-mensagem-corredor

Agora que entendemos como criar uma nova branch, vamos para os passos de enviar as mudanças que fizemos para o github.

#### Enviando minhas alterações para o remoto
Após criar sua branch e começar a trabalhar, é interessante que seja estabelecido uma frequência de commits ao fim de cada coisa que for feita na branch. Os commits permitem que você recupere o seu código caso você acabe apagando ele inteiro ou mude alguma coisa que funcionava e não sabe como consertar, para fazer commits seguimos o seguinte fluxo:

```
git add .
git comit -m "nome_do_seu_commit"
```

O comando `git add .` coloca todos os arquivos que estão *unstaged* como *staged*. Isso significa que ele pega todos os arquivos que você tem e que não eram reconhecidos pelo git e faz o git reconhecer eles, caso não tenham arquivos *staged*, o git não consegue fazer commits. O git add . também funciona com arquivos *modified*, que são arquivos que o git já reconhecia, mas que foram alterados e ele ainda não conhece essas alterações feitas. Por fim, o `git add` também pode ser usado para um arquivo específico, mas, normalmente, utilizamos ele para pegar todos os arquivos do diretório, usando o `git add .`, pois caso ele já reconheça alguns arquivos ele não pega eles novamente.

Já o comando `git commit -m` pega os seus arquivos *staged* ou *modified* e faz algo similar a guardar todos eles em um pacote, salvando a data em que isso foi feito e gerando uma chave que referencia todos esses arquivos "empacotados". Isso é feito tanto para resgatar fases específicas da nossa aplicação, quanto para enviar os arquivos para o repositório remoto.

Por fim, depois de fazer todos os commits necessários e cumprir o que era esperado na branch que trabalhou, faremos um `push`, que é o comando responsável por enviar o commit para o repositório remoto. Fazer o push é bem simples, basta fazer:

```
git push origin nome_branch
```

- push é o comando de envio para o remoto;
- origin é o nome dado ao repositório remoto do projeto, como o repositório passou a existir na máquina local por meio de `clone`, esse origin já foi gerado automaticamente;
- nome_branch é o nome da branch onde você trabalhou e fez todas as suas modificações no projeto.

#### Pull Request

Após o sucesso do seu push, vá até o github e acesse o repositório do projeto, provavelmente irá aparecer uma notificação com a cor amarela logo na parte de cima da página, indicando que você deve criar um `pull request`, clique nesse botão e siga as instruções deixadas lá, preenchendo corretamente os campos coerentes as alterações que você fez.

## Interações gerais

Depois da sua primeira interação o projeto irá continuar progredindo cada vez mais e você precisará ter todas as atualizações dele presentes na sua máquina para poder criar novos pushes, contudo, você não deve realizar um novo clone, pois o repositório já existe em sua máquina, assim seremos introduzidos a novos conceitos: `pull, merge, rebase`.

### Pull

É o comando mais importante para interações depois que você possui um clone do repositório remoto, pois ele pega todas as alterações do remoto e coloca no seu repositório local.

Ainda terminarei de escrever, mas, por enquanto, deixo aqui alguns links para entender melhor essa parte

[Git pull](https://www.atlassian.com/br/git/tutorials/syncing/git-pull)

[Git merge](https://www.atlassian.com/br/git/tutorials/using-branches/git-merge)

[Git rebase](https://www.atlassian.com/git/tutorials/rewriting-history/git-rebase)
