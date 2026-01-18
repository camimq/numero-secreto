# Anotações & conteúdos extras

# Aula 2: Colaborando em projetos

## Para saber mais: repositórios privados

**A visibilidade dos repositórios no GitHub** serve para controlar quem tem acesso a eles.

Repositórios públicos permitem que qualquer pessoa na internet os acesse, enquanto repositórios privados só podem ser acessados pelo **dono do repositório** e as pessoas que são adicionadas como **colaboradoras do projeto**.

Nas contas gratuitas do GitHub existe uma condição para o uso de repositórios privados: a quantidade de pessoas colaboradoras em cada projeto é limitada a três. Para a inclusão de mais pessoas em repositórios privados, é preciso utilizar um plano pago ou manter a visibilidade como pública.

## git init

O comando `git init` deve ser utilizado para converter um diretório existente no computador, que geralmente é o diretório de algum projeto, em um repositório Git. No entanto, seu uso requer atenção e cuidado para evitar problemas indesejados. Vamos entender melhor o que o comando `git init` faz.

### O que é o comando `git init`?

Para que possamos realizar o controle de versão de um projeto, registrando as mudanças realizadas nele ao longo do tempo, devemos, primeiramente, transformar o diretório do projeto em um repositório Git. O comando `git init` é utilizado para esse objetivo, devendo ser executado apenas **uma vez**. Quando executado, ele configura o diretório atual para ser rastreado pelo Git, inicializando um repositório vazio.

### Executando o comando `git init``

Suponha que no seu computador exista um diretório chamado `meu-projeto`, que represente um projeto pessoal seu e que você deseja transformar em um repositório do Git. Para isso, você pode abrir esse diretório no VSCode, abrir uma janela do terminal e executar o comando `git init`. A saída srá algo como:

![alt text](https://cdn1.gnarususercontent.com.br/1/4341/ea145a08-0114-4a5f-bb96-537fff10d7b5.png)

Repare na imagem anterior que o comando `git init` foi executado no terminal do VSCode. Observe também que no terminal é indicado qual o diretório no qual o comando foi executado, que no exemplo foi em: `~/Projetos/alura/meu-projeto`. É importante se atentar a isso, pois o comando `git init` transforma o diretório atual em um repositório Git, logo ele deve ser executado **dentro** do diretório do projeto e não em outros diretórios do computador.

Ao executar o comando, note que a saída no terminal foi a mensagem **`Initialized empty Git repository in /home/rodrigo/Projetos/alura/meu-projeto/.git/`**. Essa mensagem indica que o comando foi executado corretamente e um repositório local do Git foi criado com sucesso nesse diretório. A partir desse ponto, já podemos trabalhar no projeto, adicionando arquivos, realizando modificações e registrando as mudanças no Git.

### Cuidados com o comando `git init``

Aprendemos que o comando `git init` serve para criar um novo repositório Git e por isso deve ser executado apenas uma única vez. Ou seja, se um diretório já for um repositório Git, não faz sentido rodar novamento o cmando `git init`. Esse é um erro bastante comum de ser cometido.

Se você executar o comando `git init` em um diretório que já foi inicializado como um repositório Git, a seguinte mensagem será exibida:

```tex
Reinitialized existing Git repository in /home/rodrigo/Projetos/alura/meu-projeto/.git/
```

Isso indica que o Git **reinicializou** um repositório já existente, ou seja, o comando `git init` foi executado em um diretório que já era um repositório Git.

Caso você tenha cometido esse equívoco, não precisa se preocupar, pos todo o histório de mudanças e commits no projeto não serão apagados. O Git detecta que o diretório já era um repositório Git e com isso, o comando não tem efeito nenhum.

Na dúvida, antes de executar o comando `git init`, execute primeira o comando `git status`. Se aparecer a mensage, `fatal: not a git repository (or any of the parent directories): .git`, isso significa que o diretório atual **não é** um repositório Git e você pode então executar o comando `git init`.

## Git vs. Github

É muito comum confundir **Git** e **GitHub** quando estamos começando no mundo da programação. Embora seus nomes sejam parecidos e eles trabalhem juntos, eles desempenham papéis completamente diferentes no desenvolvimento de software.

Então, vamos entender as distinções fundamentais

---------

### O que é o Git, exatamente?

O git é uma **ferramenta de controle de versão**. Imagine que ele é uma "máquina do tempo" para o seu código. Ele roda localmente no seu computador e permite que você salve versões do seu projeto conforme ele evolui.

- **Onde fica:** no seu computador (local).
- **Função:** registrar alterações, criar ramificações (branches) para testar novas ideias e reverter erros.
- **Interface:** Geralmente utilizado via linha de comando (terminal).

---------

### E o que é o GitHub?

O GitHub é a **plataforma de hospedagem** na nuvem que **utiliza o Git**. Ele funciona como uma "rede social" para programadores, onde você pode guardar seus projetos (repositórios) online e colaborar com outras pessoas.

- **Onde fica:** na internet (remoto).
- **Função:** armazenar seus códigos de forma segura, permitir colaboração em equipe, revisão de código e gerenciamento de projetos.
- **Interface:** interface gráfica e amigável acessada pelo navegador.

### Resumindo

| Característica | Git | GitHub |
| :--- | :--- | :--- |
| **Natureza** | Software instalado localmente. | Serviço baseado na nuvem. |
| **Dependência** | Funciona sozinho, sem internet. | Depende do Git para funcionar. |
| **Foco** | Gerenciamento de histórico de arquivos. | Compartilhamento e colaboração. |
| **Competidores** | SVN, Mercurial. | GitLab, Bitbucket. |

Pense no **Git** como o seu **processador de texto** (como o Microsoft Word), onde você escreve e edita seu arquivo localmente. O **GitHub** seria como o **Google Drive** ou **Dropbox**, onde você envia esse arquivo para que outras pessoas vejam, comentem e ajudem a editar.

> **Dica:** você náo precisa do GitHub para usar o Git, mas o GitHub torna o uso do Git muito mais poderoso para o trabalho em equipe e para construir o seu portfólio profissional.

## Mensagens de commits

Apesar de não existir uma regra universal para a escrita das mensagens de commit, algumas boas práticas podem ser seguidas para garantir que outras pessoas, e até mesmo você no futuro, entendam que alterações foram feitas e por quê.
As mensagens dos commits devem ser simples e objetivas. A seguir, listamos algumas orientações para isso:

- **Mantenha a mensagem curta e concisa:** A primeira linha da mensagem deve conter, no máximo, 72 caracteres. Caso seja necessário uma descrição adicional, você deve pular uma linha e adicionar os detalhes, como o contexto, da mudança realizada.
- **Uso de verbo no infinitivo:** É comum que a mensagem do commit inicie com um verbo no infinitivo que descreva a alteração feita, como “adicionar”, “corrigir” ou “atualizar”. Em sequência, são adicionados detalhes concisos da mudança. Por exemplo: “Atualizar texto do título da página”.
- **Evite detalhes técnicos:** Não inclua detalhes técnicos complexos na mensagem de commit. Esses detalhes podem ser adicionados nos comentários de código ou na documentação.

É importante ter em mente que a mensagem do commit é uma forma de documentação do histórico das mudanças que ocorreram ao longo do código. A pessoa que ler essa mensagem pode não ter conhecimento do contexto original. Assim, garanta que suas mensagens de commit tenham clareza e sejam suficientemente descritivas.

## Quando realizar um commit?

Um commit deve ser realizado sempre que você **finalizar uma tarefa** específica ou resolver algum bug. Isso mantém o histórico de commits claro e rastreável, de modo que seja possível entender o que foi feito em cada commit.
Assim, é importante realizar commits frequentemente. Porém, evite realizar commits muito pequenos ou muito grandes, pois isso pode tornar difícil o seu entendimento.

Lembre-se de **nunca realizar um commit de um código que você sabe que contém bugs**. O ideal é que o commit contenha somente código funcional.

## Como o Git controla as mudanças?

O controle de mudanças do Git é feito através dos **commits**. Cada commit armazena o **estado completo** do projeto em um determinado momento por meio de um **snapshot**. Ou seja, cada commit é um registro completo do repositório no momento em que esse commit foi criado.
Como cada commit é uma representação completa e consistente do estado do projeto em um determinado ponto no tempo, isso facilita a rastreabilidade e o entendimento de como se deu a evolução do código ao longo do tempo.

Todo commit conta com um id único e traz uma referência aos commits anteriores. Assim, através dessa cadeia de commits, o Git registra um **histórico completo** de todos os commits realizados no repositório.

Caso queira conhecer melhor sobre esse processo, acesse a documentação oficial do Git.

## Adicionando colaboradores no commit

Cada commit possui por padrão um autor, que é a pessoa que realizou aquelas alterações no código.
Entretanto, quando trabalhamos em equipe pode ser que algum trecho de código seja escrito em dupla ou trio. Assim, como definir a autoria dessas outras pessoas no commit?

O Git oferece a possibilidade de adicionar **mais de um autor** a um commit. Para isso, após escrever a mensagem do commit, pulamos duas linhas e usamos a palavra-chave Co-authored-by:, seguido do nome e e-mail associado ao GitHub (entre < >) de cada pessoa colaboradora.

Cada coautor deve estar em uma linha diferente, como é mostrado no exemplo a seguir:

```text
$ git commit -m "Adicionar nova funcionalidade.
>
>
Co-authored-by: NOME <nome@email.com>
Co-authored-by: OUTRO-NOME <outro@email.com>"
```

## Outras formas de colaborar

Existem diversos projetos de software com seu código fonte disponível no GitHub e abertos para colaboração de qualquer um que queira contribuir. Esse modelo de desenvolvimento é chamado de Open Source ou Código Aberto.
Caso queira entender mais sobre projetos Open Source, temos aqui na Alura o artigo [Open Source - Uma breve introdução](https://www.alura.com.br/artigos/open-source-uma-breve-introducao), que fala mais sobre o tema.

Em um projeto que segue o modelo Open Source, as demandas, como novos recursos e correção de bugs, são descritas e listadas no repositório do GitHub via issues. Assim, caso você queira colaborar, é possível escolher uma issue.

Você precisará realizar um fork do projeto, que é uma cópia do repositório em sua conta. Assim, você poderá escrever o código que soluciona a issue escolhida.

Por fim, para enviar sua solução de volta ao repositório fonte, você precisará abrir um pull request, que é uma solicitação de pull das suas alterações. Esse pull request passará por um processo de avaliação dos responsáveis pelo projeto, podendo ser aceito ou não.

Caso seja aceito, seu código agora fará parte do código fonte desse projeto.

É importante sempre se atentar às regras de contribuição de cada repositório, que podem variar de acordo com o projeto.

Grandes projetos são Open Source e se encontram no GitHub, como a IDE VS Code e o framework React, do JavaScript. Você pode conferir os repositórios desses projetos nos links abaixo:

- [Repositório do VS Code no Github](https://github.com/microsoft/vscode)
- [Repositório do React no Github](https://github.com/facebook/react-native)

# Aula 3: Utilizando Git na IDE

## Cuidados ao mudar o histórico

Nessa aula, exploramos como é possível alterar o histórico de commits no Git, mas é fundamental exercer cautela ao realizar tais mudanças. Como diz o ditado, "com grandes poderes vêm grandes responsabilidades".
É importante destacar que os comandos do Git que permitem modificar o histórico de commits devem ser utilizados com prudência e apenas quando o commit em questão ainda não foi enviado ao repositório remoto, ou seja, quando ele existe apenas no seu repositório local.

Modificar um commit que já se tornou público, ou seja, aquele que já foi enviado ao GitHub ou a qualquer outro repositório remoto, pode acarretar problemas consideráveis na colaboração com as outras pessoas e na integridade do histórico de um projeto.

Em situações de colaboração em equipe, é essencial manter a integridade do histórico de commits, pois qualquer modificação em um commit que outras pessoas estejam trabalhando pode resultar em conflitos e dificuldades na colaboração.

É recomendável evitar a modificação excessiva do histórico de commits, uma vez que isso pode tornar o histórico confuso. O histórico deve ser uma representação precisa do progresso do projeto ao longo do tempo.