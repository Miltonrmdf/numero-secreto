Gabrielle: Já instalamos o Git e inicializamos o repositório local com o comando git init. Mas agora, como podemos prosseguir para conectar esse repositório local ao repositório remoto no GitHub.

Rodrigo: Isso é muito importante. O Git possui esse conceito de repositório local e repositório remoto. Quando criamos o repositório no GitHub, o repositório que se encontra lá é denominado repositório remoto. No entanto, em nosso computador, também precisamos criar um repositório, que será o local.

Esses dois repositórios não estão conectados. Agora que instalamos o Git e criamos o repositório local, podemos seguir o tutorial que foi apresentado para estabelecer essa conexão entre o meu repositório local e o repositório remoto no GitHub.

Adicionar arquivos e vincular repositório
Rodrigo: Vamos retornar ao site do GitHub. Já executamos o comando git init. O próximo comando que aparece no tutorial é git add, que mostra como exemplo um arquivo README.md que não possui existe no nosso projeto. Ao invés disso, precisamos adicionar os arquivos do nosso projeto.

Vamos copiar o comando git add e o colar no terminal integrado do VS Code. No entanto, precisamos adicionar cada um dos arquivos do projeto. Mas, temos vários arquivos neste projeto, como o app.js, index.html e outros. Precisaremos adicionar cada um manualmente?

Gabrielle: Temos a opção de adicionar manualmente, informando o nome de cada um dos arquivos, mas às vezes pode ser um pouco trabalhoso, especialmente quando temos um projeto grande com muitos arquivos.

Para facilitar esse processo, temos um atalho no comando do Git, onde podemos adicionar todos os arquivos de uma só vez. É o comando git add .. Esse ponto vai adicionar todos os arquivos do repositório.

git add .
Copiar código
Rodrigo: Após pressionar "Enter", apareceram alguns alertas, porque existem algumas diferenças entre Windows e Linux, dependendo do sistema operacional que você estiver utilizando. No entanto, são só alertas e não vão afetar nada.

Retornando ao GitHub, o próximo comando que encontramos é o git commit -m e temos que inserir uma mensagem entre aspas. Copiamos até o -m, porque vamos alterar a mensagem. Colocaremos a mensagem projeto inicial entre aspas duplas.

git commit -m "projeto inicial"
Copiar código
Estes comandos, add e commit, foram somente copiados e executados, mas nas próximas aulas, vamos explicar detalhadamente o que cada um faz. No momento, o objetivo é apenas conectar os dois repositórios: o local no computador com o remoto no GitHub.

Author identity unkown

Após pressionar "Enter", houve um erro ao tentar fazer o commit.

Gabrielle: Apareceu uma mensagem indicando que a identidade do autor desse commit é desconhecida. Precisamos fazer uma configuração para informar quem é a pessoa responsável por esse commit.

No terminal, é exibida uma dica indicando quais comandos devemos usar para fazer essa configuração:

git config --global user.email "your@example.com"
git config --global user.name "Your Name"
Copiar código
Rodrigo: No GitHub, criamos uma nova conta e fiz o login. Portanto, o GitHub sabe quem somos, porque estamos logados no navegador. No entanto, instalamos o Git no computador e o Git não sabe quem somos, pois não possui vínculo direto com o GitHub.

Esses comandos são justamente para nos identificar ao Git no computador.

Copiamos apenas comando git config --global user.email, mas só até email. Vamos colar no terminal e incluir o e-mail que configuramos no GitHub. No nosso caso, é o rodrigo.alura87@gmail.com entre aspas duplas.

git config --global user.email "rodrigo.alura87@gmail.com"
Copiar código
Atenção: Você deve substituir pelo e-mail usado para criar sua conta no GitHub!

Após pressionar "Enter", vamos utilizar a seta para cima para resgatar o último comando digitado. Alteraremos o user.email para user.name, pois além do e-mail, o Git também precisa saber o seu nome.

Entre as aspas, inserimos o Rodrigo Ferreira e apertamos "Enter". Você deverá colocar seu nome e sobrenome.

git config --global user.name "Rodrigo Ferreira"
Copiar código
Pronto. Realizamos a configuração de maneira global, devido a esse parâmetro --global. Agora, neste computador, qualquer repositório que criamos, o Git já nos reconhece.

Gabrielle: Agora, podemos prosseguir e tentar realizar esse commit.

Rodrigo: Vamos apertar novamente a seta para cima três vezes para voltar para o comando de commit e dar um "Enter". Agora o commit foi realizado.

[master (root-commit) 250c665] projeto inicial

10 files changed, 334 insertions (+)

Ele registrou esses arquivos no nosso repositório local. Ótimo, vamos voltar para o tutorial no GitHub.

O próximo comando, git branch -M main. Vamos copiar, colar e executar. Não deu nenhum alerta.

git branch -M main
Copiar código
E o próximo comando é o principal, pois é o comando que vai fazer o vínculo do repositório do GitHub com o meu repositório local, que é esse git remote add.

Gabrielle: Sim, após executar esse comando, vamos conseguir que esse repositório que temos localmente em nosso computador esteja conectado com esse repositório do GitHub.

Rodrigo: Vamos apenas fazer uma alteração, porque por padrão ele vem com o protocolo HTTPS. Mas acima, onde temos instruções para o Quick Setup (configuração rápida), tem um botão chamado "SSH". Se clicamos neste botão, o GitHub troca para o protocolo para o SSH.

Geralmente, o protocolo SSH é o mais recomendado para fazer esse ligação com o GitHub.

O comando git remote add origin já foi alterado, e agora a URL não está com http://. Ela está usando o formato SSH. Vamos copiar e colar no terminal integrado:

git remote add origin git@github.com:rodrigoalura87/numero-secreto.git
Copiar código
Lembre-se que a URL do GitHub vai variar de acordo com o nome do seu usuário e projeto!

Gerar chave SSH
Por fim, temos o comando para enviar esses arquivos, ou seja, esse commit que fizemos localmente para o GitHub com o comando git push. O remote add não envia automaticamente, ele só faz a ligação.

git push -u origin main
Copiar código
Vamos copiar e colar esse último comando. Com isso, ele vai tentar sincronizar, de fato, com o GitHub. Vamos conferir se vai funcionar.

The authenticity of host 'GitHub.com (20.201.28.151)' can't be established

Deu outro erro! Foi um erro de autenticação. Afinal, instalamos o Git no computador, colocamos o e-mail e nome, mas como é que o GitHub vai saber que somos nós mesmos - e não é outra pessoa que está usando nosso nome e e-mail?

De alguma forma, precisamos fazer essa configuração de segurança para ele saber que neste computador, é, de fato, o Rodrigo com e-mail específico e está vinculado com a conta do Rodrigo no GitHub.

Como copiamos o protocolo SSH, o Git já nos dá a sugestão de gerar uma chave SSH no computador porque ainda não temos uma. Ele faz uma pergunta que precisamos responder com "sim" ou "não".

Are you sure you want to continue connecting (yes/no/[fingerprint])?

Em inglês, ele pergunta: quer continuar a conexão? Respondemos com um yes (sim). Feito isso, ele manda uma mensagem dizendo que não reconhece esse computador, portanto, não está autorizado para se conectar no GitHub.

Warning: Permanently added 'github.com' (ED25519) to the list of known hosts

git@github.com: Permission denied (publickey)

Isso é importante para garantir a segurança. Ou seja, vamos ter que fazer essa configuração no GitHub.

Gabrielle: Isso mesmo. Vamos ao GitHub finalizar essa configuração.

Rodrigo: Essas são configurações iniciais, pois como acabamos de instalar o Git, não tem nada disso configurado. Será apenas uma vez que precisamos fazer todos esses comandos.

De volta ao GitHub, no canto superior direito da página, vamos clicar no ícone do avatar para abrir o menu lateral e selecionar a opção "Settings". Assim, entraremos nas configurações da nossa conta e não do repositório.

Na página de configurações da nossa conta, no menu à esquerda, existe a opção "SSH and GPG keys" onde podemos fazer a configuração do SSH.

Em seguida, vamos clicar no botão verde "New SSH key" (nova chave SSH). Ao clicar nesse botão, devemos colocar um título. É como se estivéssemos criando uma chave para conectar esse nosso computador com o GitHub. Vamos colocar notebook pessoal, apenas para identificar que chave é essa.

Ele também solicita um tipo, nesse caso, é uma chave de autenticação (Authentication key). Além disso, nos orienta a colar a chave. Mas, de onde vamos conseguir essa chave, Gabi?

Gabrielle: Devemos gerar essa chave em nosso computador.

Rodrigo: Assim, no nosso computador, teremos que acessar essa chave que foi gerada com o SSH.

No terminal integrado, quando pressionamos "yes", ele deve ter criado uma chave que fica salva dentro do computador na pasta do usuário. Podemos tanto fazer isso pelo terminal ou navegar até a pasta, o que é mais fácil.

Portanto, vamos abrir o explorador de arquivos e entrar na pasta do usuário. Nesse casso, a pasta Rodrigo. Agora, vamos procurar uma pasta oculta chamada .ssh. Entrando nela, há um arquivo chamado known_hosts, que são os hosts conhecidos, mas a chave não foi gerada.

Para gerar a chave, existe um comando que temos que copiar. Inclusive, existe um tutorial no próprio site do GitHub, que vamos disponibilizar no curso como uma atividade. Ele tem um tutorial ensinando como gerar uma chave SSH para cada sistema operacional. No nosso caso, é o Windows.

Nessa documentação, temos a explicação do que é e como gerar uma chave SSH. Vamos copiar o comando sugerido ssh-keygen -t ed25519 -C seguido do e-mail da conta do GitHub.

No terminal do Visual Studio Code, vamos colá-lo. Porém, temos que alterar o e-mail de exemplo para o nosso e-mail, que é rodrigo.alura87@gmail.com. Você deve substituir com seu e-mail pessoal.

ssh-keygen -t ed25519 -C "rodrigo.alura87@gmail.com"
Copiar código
Após apertar "Enter", ele informa que vai gerar um par de chaves SSH. E nos pergunta onde queremos salvar esse arquivo.

Enter file in which to save the key (C:\User\Rodrigo/.ssh/id_ed25519):

Você pode simplesmente pressionar "Enter" para salvá-lo na própria pasta SSH, que é a pasta padrão. Ele pergunta se você quer digitar uma senha.

Enter passphrase (empty for no passphrase):

Se digitamos uma senha, toda vez que eu for sincronizar com o GitHub, ele vai nos pedir essa senha. Por isso, vamos apenas pressionar "Enter" para não ter uma senha. Depois, devemos digitar a mesma senha novamente, damos "Enter" novamente.

Pronto. Agora a chave foi gerada.

Vamos até a pasta "Rodrigo > .ssh". Agora, contém dois arquivo chamamos id_ed25519, um com a chave privada, outro com a chave pública. Devemos abrir o da chave pública, vamos conferir.

Vamos dar dois cliques e mandar abrir com o bloco de notas. Estava escrito private key, era a chave privada.

Vamos abrir o outro arquivo. Podemos clicar com o botão direito e selecionar "Abrir com" e escolher o aplicativo de bloco de notas. Agora, temos o código da chave começando com ssh ed-25519 que precisamos copiar e colar no site do GitHub.

No campo key, vamos colá-lo e apertar o botão "Add SSH Key" para adicionar a chave SSH. O GitHub já adicionou e listou a chave do notebook pessoal em "SSH keys".

Agora o GitHub sabe que neste notebook tem uma chave e já nos autenticamos, pois geramos essa chave com o nosso e-mail. Assim, o GitHub confia neste computador. Desse modo, conseguiremos sincronizar com a nossa conta no GitHub.

Sincronizar repositórios
Rodrigo: Vamos voltar para o Visual Studio Code e tentar fazer novamente aquele git push:

git push -u origin main
Copiar código
Vamos conferir se agora vai funcionar.

Total 14 (delta 0), reused 0 (delta 0), pack-reused 0

To github.com: rodrigoalura87/numero-secreto.git

[new branch) main -> main
branch 'main' set up to track 'origin/main'.

Finalmente, o upload dos arquivos e do commit para o nosso repositório no GitHub foi bem-sucedido, ao que tudo indica. Será que está sincronizado, Gabi?

Gabrielle: Sim, aparentemente funcionou, mas vamos abrir nosso repositório no navegador e atualizar a página para verificar se encontramos nosso projeto lá?

Rodrigo: No navegador, precisamos voltar para a página do repositório. Basta clicar no ícone do avatar e acessar "Your repositories" (seus repositórios) e escolher o numero-secreto. Em seguida, vamos atualizar a página (atalho "F5") e o projeto apareceu.

O tutorial que estava antes sumiu, porque agora tudo já está sincronizado e os arquivos estão sincronizados no repositório remoto.

Temos o index.html, o app.js e o sistema identificou o commit e usuário, o rodrigoalura87. Podemos navegar pelos arquivos e ter acesso ao código-fonte.

Logo, nosso repositório está sincronizado e na barra de endereços temos a URL do repositório. No nosso caso, é github.com/rodrigoalura87/numero-secreto.

Podemos compartilhar esse link com outras pessoas e elas podem acessar o repositório, inclusive você, Gabi. Eu posso te enviar este repositório e fica aí essa pergunta: será que você conseguirá baixar o projeto no seu computador?

Gabrielle: O GitHub nos proporciona essa possibilidade de outras pessoas não apenas acessarem nosso código, mas também contribuírem para ele. Vamos explorar isso em seguida.

---------------------------------------------------

O comando git push deve ser executado para sincronizar as mudanças do repositório local com o repositório remoto, ou seja, quando desejamos enviar os novos commits que realizamos em nosso repositório local para o repositório remoto. No entanto, para garantir uma conexão segura, é essencial configurar uma chave SSH no computador antes de executar esse comando.

Chave SSH
Ao vincular um repositório remoto ao nosso repositório local, via comando git remote add, precisamos utilizar algum protocolo seguro, como HTTPS ou SSH. No caso de se utilizar o protocolo SSH, escolha realizada neste curso, devemos gerar uma chave SSH em nosso computador, além de cadastrá-la em nossa conta do GitHub. Isso é necessário para garantir a autenticação, pois o GitHub checa se quem está realizando o push dos commits tem permissão para realizar tal ação.

Geração de uma chave SSH
Antes de executar o comando git push, precisamos gerar uma chave SSH. A geração da chave é feita via terminal, com o comando ssh-keygen -t ed25519 -C "SEU EMAIL AQUI":

Terminal do VSCode com o comando ssh-keygen -t ed25519 -C "fulano@email.com.br" sendo executado.

Repare, na imagem anterior, que ao executar o comando para gerar uma chave SSH, uma pergunta foi feita e o terminal fica travado esperando nossa resposta:

Generating public/private ed25519 key pair.
Enter file in which to save the key (/home/rodrigo/.ssh/id_ed25519):
Copiar código
Essa primeira pergunta é para indicarmos o diretório em nosso computador no qual a chave será salva, sendo que entre parênteses é indicado o diretório padrão. O recomendado é apenas apertar a tecla enter no teclado para que a chave seja salva no diretório padrão, pois assim o Git consegue encontrar essa chave automaticamente sempre que executarmos o comando git push.

Após apertar a tecla enter, uma nova pergunta será apresentada no terminal:

Enter passphrase (enter for no passphrase):
Copiar código
Essa segunda pergunta é para indicarmos se desejamos adicionar uma senha à chave SSH que será gerada. Caso você digite uma senha, toda vez que executar o comando git push será necessário digitar tal senha. Ao não digitar nada e apenas apertar a tecla enter, a chave será gerada sem a proteção de uma senha.

Por fim, a terceira e última pergunta é apenas para confirmar a senha anterior:

Enter same passphrase again:
Copiar código
A chave será gerada e a seguinte mensagem será exibida no terminal:

Your identification has been saved in /home/rodrigo/.ssh/id_ed25519
Your public key has been saved in /home/rodrigo/.ssh/id_ed25519.pub
The key fingerprint is:
SHA256:jxAkhGR7NHm/0fcmyPnErZxSKr+ObsH7r4AC/vUNvPY fulano@email.com.br
The key's randomart image is:
+--[ED25519 256]--+
| .oo=..          |
| ..o.+.          |
|  . .... .       |
|   .   .o . .    |
|  .   ..S+ = o   |
| . .   ++o+ = +  |
|  . . o =o.* =   |
|   . o .=*o =    |
|    .  +=*E=.    |
+----[SHA256]-----+
Copiar código
Na primeira linha da mensagem você consegue identificar o diretório no seu computador no qual a chave foi salva. Agora, basta acessar tal diretório para ter acesso à chave SSH.

Observação: Nesse diretório serão gerados dois arquivos que representam a chave SSH, sendo um para a chave privada (arquivo id_ed25519) e o outro para a chave pública (id_ed25519.pub).

Cadastrando a chave SSH no GitHub
Após gerar a chave, precisamos cadastrá-la em nossa conta do GitHub, para que assim o GitHub consiga nos identificar e autenticar ao executar o comando git push de nosso computador.

Acesse a página de chaves SSH de sua conta no GitHub e clique no botão New SSH key ou Nova chave SSH para realizar o cadastro da chave:

Formulário para cadastro de chave SSH no site do GitHub, contendo os campos "title", "key type" e "key".

Repare que o formulário exibido na imagem anterior contém três campos:

Title ou Título: Informe um apelido para sua chave SSH (por exemplo: computador casa)
Key type ou Tipo de chave: Escolha o tipo Authentication Key ou Chave de autenticação
Key ou Chave: Nesse campo você deve colar o conteúdo do arquivo da sua chave SSH pública (arquivo id_ed25519.pub)
Após realizar esse procedimento, será possível sincronizar o repositório local com o remoto, enviando os novos commits com o comando git push.

----------------------------------------------------

Vimos no vídeo anterior que para fazer o link entre o repositório local, que está em nosso computador, com o repositório remoto, que está no GitHub, devemos utilizar o comando git remote.

Esse comando tem algumas variações e parâmetros opcionais que podem ser úteis em certas situações. Confira a seguir exemplos de uso desse comando:

1 - Adicionar um repositório remoto:

Quando você deseja estabelecer uma conexão entre seu repositório local e um repositório remoto, como aquele hospedado no GitHub, o comando git remote add é a ferramenta essencial. Essa etapa é crucial para possibilitar a colaboração e o compartilhamento de código com outras pessoas, bem como para fazer backup de seu trabalho em um servidor remoto.

A sintaxe básica do comando é a seguinte:

git remote add apelido url
Copiar código
'apelido': Este é um nome que você atribui ao repositório remoto. Geralmente, se utiliza nomes descritivos, como "origin" para o repositório principal no GitHub, mas você pode escolher nomes que façam sentido para o seu projeto.

'url': Aqui, você insere a URL do repositório remoto. Esta URL é única para cada repositório remoto e serve como o endereço para acessar e interagir com ele pela internet. Certifique-se de copiar a URL correta do repositório que deseja adicionar.

2 - Listar os repositórios remotos:

Para listar os repositórios remotos associados ao seu projeto local, você pode utilizar o comando git remote -v. Isso exibirá uma lista de todos os repositórios remotos vinculados ao seu projeto, juntamente com suas URLs. Veja um exemplo:

git remote -v
Copiar código
A saída será algo semelhante a:

origin   https://github.com/seu-usuario/seu-projeto.git (fetch)
origin   https://github.com/seu-usuario/seu-projeto.git (push)
Copiar código
Essa lista é útil para verificar se os repositórios remotos estão configurados corretamente. Obs: Vai aparecer duplicado mesmo, pois o Git separa a url de envio de commits (push) da url de baixar commits (fetch).

3 - Remover um repositório remoto:

Caso você não precise mais de um repositório remoto específico, pode removê-lo com o comando git remote remove apelido. Substitua 'apelido' pelo nome do repositório remoto que deseja remover. Aqui está um exemplo:

git remote remove origin
Copiar código
Após a execução deste comando, o repositório remoto chamado "origin" será desvinculado do seu projeto local.

4 - Alterar a URL de um repositório remoto:

Às vezes, é necessário atualizar a URL de um repositório remoto, como quando a URL do servidor do GitHub é modificada ou quando você copiou a URL incorreta ao adicionar o repositório remoto. Use o comando git remote set-url apelido nova_url para realizar essa atualização. Substitua 'apelido' pelo nome do repositório remoto e 'nova_url' pela nova URL que você deseja associar a ele. Aqui está um exemplo:

git remote set-url origin https://github.com/seu-usuario/seu-repositorio.git
Copiar código
Isso atualizará a URL do repositório remoto "origin" para a nova URL especificada.

5 - Alterar o apelido de um repositório remoto:

Se você deseja renomear um repositório remoto, use o comando git remote rename apelido novo_apelido. Substitua 'apelido' pelo nome atual do repositório remoto e 'novo_apelido' pelo novo nome que você deseja atribuir a ele. Aqui está um exemplo:

git remote rename origin novo-origin
Copiar código
Isso renomeará o repositório remoto de "origin" para "novo-origin".

Lembre-se de que o comando git remote é fundamental para a gestão de conexões entre seu repositório local e repositórios remotos, permitindo a colaboração eficiente e o controle de versão. Praticar esses comandos em seu ambiente de desenvolvimento ajudará a consolidar seu entendimento.

______________________________________
Nesse curso, aprendemos como realizar a autenticação no Github em seu computador pessoal através de uma chave SSH. Entretanto, essa não é a única forma de se autenticar no Github.

Caso você tente conectar seu repositório local com o repositório remoto através da conexão HTTP, será pedido uma senha no momento de realizar o seu login. Porém, desde 2021, por motivos de segurança, o Github não aceita mais que essa autenticação seja feita por meio de sua senha.

Caso você tente usar sua senha, acontecerá um erro como o mostrado a seguir:

Logon failed, use ctrl+c to cancel basic credential prompt.
remote: Support for password authentication was removed on August 13, 2021. Please use a personal access token instead.
remote: Please see https://github.blog/2020-12-15-token-authentication-requirements-for-git-operations/ for more information.
fatal: unable to access ‘<repositório Git>’: The request URL returned error: 403 
Copiar código
Assim, a outra opção de autenticação para usar o Github em seu terminal é através de um token para o git.

O artigo Nova exigência do Git de autenticação por token, o que é e o que devo fazer? te ensinará a realizar as configurações necessárias para criar e utilizar esse token.
________________________________________________________________
O Git é uma ferramenta excelente para acompanhar a mudança entre versões de um mesmo projeto e, dentre vários benefícios, nos ajuda a observar de perto o desenvolvimento do seu aprendizado. Tudo isso de uma forma organizada através dos commits.

Além disso, algo que é essencial no universo da tecnologia é apresentar o seu progresso para a comunidade e montar um portfólio dos seus projetos para demonstrar suas habilidades. Dessa forma, o GitHub é essencial para compartilhar e colaborar em projetos de programação de todo o mundo.

Pensando nisso, criamos uma lista de atividades (não obrigatórias) focada em prática para melhorar ainda mais sua experiência de aprendizagem. Bora praticar então?

Desafios
Crie uma conta no GitHub
Crie um repositório para um projeto pessoal.
Faça a instalação do Git
Crie um repositório localmente para o seu projeto pessoal
Adicione alguns arquivos no seu repositório local
Faça o commit das alterações
Configure a identidade do autor do commit.
Crie a branch Main
Realize a conexão do seu repositório local com o remoto
Envie as alterações no repositório local para o remoto
Utilize o comando git status
Caso precise de ajuda, opções de solução das atividades estarão disponíveis na seção “Opinião da pessoa instrutora”.
_______________________________________
Opinião do instrutor

Crie uma conta no GitHub Você pode começar seguindo os passos mostrados no vídeo, preenchendo o formulário de cadastro, verificando sua conta e explorando a página inicial do GitHub.

Criar um novo repositório no GitHub e fazer o upload de um projeto local para esse repositório. Você pode seguir passos mencionados na aula, como acessar as configurações do GitHub, criar um novo repositório com um nome único e escolher se ele será público ou privado. Em seguida, você pode adicionar uma descrição, um README, um .gitignore e uma licença ao repositório.

Instalação do Git: Caso você ainda não tenha realizado a instalação, siga os passos na atividade Faça como eu fiz: instalação do Git

Para criar um repositório local você, digite o seguinte comando no terminal: git init

Para adicionar os arquivos no repositório local, digite no terminal o comando: git add .

Faça um commit com as modificações, digite no terminal o comando: git commit -m "mensagem de commit"

Para configurar a identidade do autor do commit, digite no terminal o comando:

git -config --global user.email "seuemailaqui@example.com"
git config --global user.name "seu nome aqui"
Copiar código
Para criar a branch Main, digite no terminal o comando: git branch -M main

O comando git branch -m é usado para criar uma nova ramificação no repositório Git atual. Neste caso, criamos a branch padrão main, que representa a versão principal do código.

Para realizar a conexão do seu repositório local com o remoto via SSH, digite no terminal: git remote add origin git@github.com:seunomedeusuario/seu-repositorio.git

Caso seja necessário, realize a configuração do protocolo SSH através da geração de chave, você pode acompanhar os passos em vídeo na atividade Sincronizando repositórios

Para subir as alterações no repositório local para o remoto, digite o seguinte comando no terminal: git push -u origin main

Digite no terminal o comando git status e observe a saída.

O comando git status é uma ferramenta essencial para gerenciar alterações no controle de versão Git. Ele fornece uma visão geral do estado atual do repositório, indicando quais arquivos foram modificados, adicionados ou excluídos desde o último commit. Essa informação é crucial para compreender o progresso do desenvolvimento e tomar decisões de gerenciamento de alterações.

A saída do comando git status geralmente contém três seções principais:

Modificados: Lista os arquivos que foram modificados desde o último commit, mas ainda não foram adicionados à área de preparação (Stage).

Adicionados: Indica os arquivos que foram adicionados à área de preparação, mas ainda não foram confirmados no histórico de commits.

Modificados, adicionados ou excluídos: Exibe os arquivos que não foram rastreados pelo Git, ou seja, que não foram adicionados ao índice de modificações (Staging Area).

Além disso, o comando git status pode fornecer informações adicionais sobre as ramificações atuais, como a ramificação atual e as ramificações que estão à frente ou atrás da atual.

O comando git status é uma ferramenta indispensável para qualquer desenvolvedor que utiliza Git. Ele permite monitorar as alterações no repositório, identificar o estado dos arquivos e tomar decisões de gerenciamento de commits de forma eficiente


+++++++++++++++++++++++++++++++++++++++++++++++

Quando você está trabalhando em um projeto grande, principalmente se muitas pessoas estão envolvidas, é comum aparecerem os chamados "conflitos". Mas o que são esses conflitos?

Imagine que o projeto é um grande quebra-cabeça e cada pessoa está trabalhando em uma parte dele. Se duas pessoas tentarem encaixar peças diferentes no mesmo lugar, surge um conflito. No mundo do desenvolvimento de software, isso ocorre quando duas pessoas editam o mesmo pedaço de código de formas diferentes.

Há várias formas de resolver conflitos, podemos utilizar a linha de comando ou o próprio Visual Studio Code. O editor de código fornece mais de uma forma para resolver conflitos de mesclagem entre o código local (o que está na sua máquina) e o remoto(o que está no github, por exemplo).

Uma possibilidade é utilizar a ferramenta “Merge Editor”. Vamos conferir seu funcionamento?

Resolvendo conflitos no Merge Editor
No exemplo a seguir, nós temos duas versões de um código na branch main: uma no repositório do github e outra modificação diferente no ambiente local. Ao realizarmos o git -push para a branch main, ocorreu um conflito e precisamos resolvê-lo para que a atualização suba para o repositório no github corretamente, como a imagem nos apresenta:

 Para solucionarmos o problema, clicamos na opção “Resolve in Merge Editor”, como no print abaixo:

Captura de tela que apresenta um botão com o texto "Resolve in Merge Editor"

Após o clique, somos redirecionados para outra aba que apresenta as modificações no arquivo, vamos entender o que cada opção significa:

Uma captura de tela representando o editor de mesclagem, uma ferramenta usada para resolver conflitos e mesclar versões de código de maneira integrada. Temos uma nova aba chamada "merging: index.html". Há a divisão da tela em três partes: Incoming, Current, Result. No canto inferior direito da tela há um botão "complete merge"

A tela do Visual Studio Code está dividida em três partes:

Incoming (remoto): modificações que chegam do repositório remoto.

Current (local): modificações locais.

Result (resultado): resultado do merge, ou seja, a resolução dos conflitos de mesclagem. É o estado atual do arquivo.

Os quadrados na cor amarela em volta do código no campo “Incoming” e “Current” são marcadores de conflito: exibem o conteúdo que apresenta conflito no arquivo.

Campo Incoming
-> No campo “Incoming”, acima da linha de código dos marcadores de conflito no campo há outras opções que resultam na alteração do código atual:

Accept Incoming: aceita modificações oriundas do remoto
Captura de tela com o campo Incoming, Current, e o Result com o código do campo Incoming

Accept Combination Incoming First: realiza a combinação com as linhas do código do repositório remoto no topo.
Captura de tela com o campo Incoming, Current, e o Result com o código do campo Incoming e Current respectivamente

Ignore: ignora as modificações.
Campo Current
-> O campo “Current” trabalha com as modificações locais do documento.

Accept Current: Aceita a modificação local no resultado do documento

Accept combination Current First: Aceita a combinação local + remoto. Nos resultados a linha de código com a tag <h2> fica antes de <h1>, comprovando que o código local é inserido primeiro que o remoto.

Captura de tela com o campo Incoming, Current, e o Result com o código do campo Current e Incoming respectivamente

Ignore: ignora as modificações no resultado no final.
Após selecionarmos a opção com o resultado desejado, devemos:

Salvar o arquivo
Clicar no botão “complete Merge”
Realizar o commit das modificações
Sincronizar as modificações realizando o push.
Para saber mais:
Como o Visual Studio facilita o controle de versão com o Git

Como resolver conflitos de mesclagem no Visual Studio

Um guia muito útil para mesclar conflitos - em Inglês


_______________________________________________
Transcrição
Rodrigo: Bom, Gabi, já aprendemos vários recursos do GitHub e do Git. Contudo, até agora, focamos mais na parte de colaboração.

Criei um repositório no meu usuário do Git, você fez o clone, te adicionei como colaboradora e começamos a trabalhar simulando rotinas de desenvolvimento de software. Você realizou mudanças no código, commits, assim como eu no meu computador, baixando os seus commits e enviando os commits para o GitHub.

Cada commit representa uma versão do código, que fica registrada no histórico. Conhecemos o git-log e conseguimos conferir todo o histórico de versões. E, eventualmente, vamos querer voltar no tempo, pois alguém pode pedir para desfazer uma alteração. O Git também nos ajuda com esta situação, correto?

Gabrielle: Sim, o Git pode nos ajudar nessas situações. Notei que você fez uma nova modificação no nosso projeto. Havia a imagem de uma menina ao fundo e você a removeu. Agora, vamos supor que queremos trazer essa imagem de volta, retornar para a versão em que tínhamos essa imagem no projeto. Como podemos fazer isso?

Rodrigo: Neste caso, poderíamos entrar no site do GitHub, clicar na lista do log para ver os commits e encontrar qual foi o commit que fez essa alteração. Lembre-se de que é possível detalhar o que aquele commit fez no código e quais arquivos foram modificados.

Neste nosso exemplo, seria simples encontrar as alterações, porque a mudança ocorreu apenas no index.html. Porém, e se o commit tivesse alterado 86 arquivos, por exemplo? Não seria nada produtivo ter que verificar arquivo por arquivo, ir ao VS Code e desfazer a alteração.

Presumo que o Git tenha um comando para automatizar esse processo, certo, Gabi?

Gabrielle: Isso mesmo. Vamos descobrir qual é esse comando?

Vamos abrir o VS Code e, naquela ferramenta do GitHub que estávamos utilizando no próprio VS Code, para abrir o log, aquele histórico dos nossos commits. A ferramenta é a "Source Control", no terceiro botão do menu lateral esquerdo.

Clicando nessa ferramenta, temos o menu de três pontos (botão "Views and More Actions"). Vamos clicar nele e verificar se temos a opção de log. Procurando nas opções, não vemos nenhuma que mostre nosso histórico de commits.

Rodrigo: Verdade. Começamos a usar essa integração do Visual Studio Code com o Git, mas nem todos os comandos estão disponíveis via menu. Os mais comuns, como ver o status, qual arquivo foi modificado, fazer um commit, ADD, push, pull, são exibidos.

Mas, se quisermos executar um log ou outros comandos mais avançados, e que não são tão comuns, o VS Code não mostra. Sendo assim, teremos que usar o terminal novamente.

Gabrielle: Vamos abrir novamente o terminal, clicando em "Terminal > New Terminal" no menu superior. Vamos minimizar o menu lateral esquerdo para deixar apenas o terminal na tela.

Agora, vamos rodar o comando git log, que já conhecemos. Como vimos anteriormente, esse comando traz algumas informações dos nossos commits. Cada commit possui um ID, o qual identifica esse commit de maneira única.

Rodrigo: O ID único é a maneira pela qual o Git diferencia cada commit. É como se fosse um ID de registro no banco de dados. Precisamos saber qual é o commit que queremos desfazer e, para isso, usaremos esse ID.

Gabrielle: O commit que queremos desfazer é o "removendo foto", então vamos copiar o ID dele (o código de letras e números ao lado de "commit").

commit 2ad48c068dc9677fb57efec70620700410f976b0
Copiar código
Em seguida, pressionamos a tecla "Q" para retornar ao nosso terminal. O comando para reverter um commit é o git revert, passando ao lado o ID do commit a ser desfeito.

git revert 2ad48c068dc9677fb57efec70620700410f976b0
Copiar código
Rodrigo: Executando o comando git revert, é aberta uma pequena janela no topo da tela. Isso acontece porque o git revert é o comando responsável por realizar o processo de identificar o commit pelo ID passado como parâmetro, analisar cada alteração feita por ele e desfazer essas alterações sozinho.

Entretanto, o revert não desfaz as alterações modificando apenas os arquivos. Ele cria um novo commit para registrar esse revert.

Gabrielle: Portanto, o revert já nos fornece uma mensagem para esse novo commit,dizendo que realizou um revert e traz a mensagem do commit original, por exemplo, além do ID desse commit.

Revert "removendo foto"

This reverts commit 2ad48c068dc9677fb57efec70620700410f976b0.

Fechando esta janela, essa mensagem já ficará salva para o novo commit.

Agora, vamos executar o comando git log no terminal para verificar o que aconteceu.

Na lista de commits, foi retornado esse novo commit no topo da lista, indicando que ocorreu um revert do commit de "removendo foto".

Rodrigo: Então, na verdade, o revert não apaga o commit original. O que ele faz é criar um novo commit que efetua uma espécie de "Ctrl + Z" no commit original. Todos os arquivos modificados pelo commit original têm suas alterações desfeitas, mas o revert fica registrado no histórico.

No entanto, como é um novo commit, ele está apenas no nosso repositório local. Portanto, quisermos enviá-lo para o GitHub, será necessário sincronizar, rodando novamente o seguinte comando no terminal:

git push origin main
Copiar código
Com isso,sincronizamos e enviamos esse commit de revert para o repositório remoto, permitindo que outras pessoas possam baixá-lo.

Será que essa alteração funcionou? Vamos verificar no site se a foto da pessoa foi restaurada

Gabrielle: Abrindo o navegador, podemos notar que a imagem da menina já está no plano de fundo novamente. Portanto, deu certo!

Rodrigo: Nós fizemos o revert, desfizemos a alteração de um determinado commit. O próprio git se encarregou de olhar cada arquivo, desfazer as respectivas alterações e registrar isso no histórico, revertendo o código para a versão anterior.

Esta é uma situação comum. Eventualmente, as pessoas que usam o sistema podem solicitar uma alteração e, depois de uma semana ou um mês, elas podem mudar de ideia e dizer:

— Olha, testamos a alteração que você fez naquele dia, e não era exatamente o que queríamos. Você pode reverter para o como estava antes?

E nós não lembraremos de cabeça como era o código anterior. Portanto, graças a essa funcionalidade de registro por commits, nós conseguimos localizar este commit e fazer o revert, recuperando a versão do código daquele momento.

Gabrielle: O histórico de comandos pode ser útil em outras situações. Por exemplo, vamos imaginar que em vez de querer reverter um commit, tenhamos feito algo no repositório local e queiramos excluir esse commit, removê-lo do histórico. É possível fazer isso?

Rodrigo: Essa é uma situação diferente. Agora não queremos mais apenas desfazer um commit, mas de fato apagá-lo. É possível fazer isso, e aprenderemos a seguir.

________________________________________________________________________

Transcrição
Rodrigo: No último vídeo, aprendemos como desfazer um commit utilizando o comando git revert. Esse comando gera um novo commit com essa mudança, desfazendo todo o código que foi alterado naquele determinado commit.

No entanto, existem situações em que não queremos, de fato, desfazer um commit. Na verdade, queremos apagar o commit do histórico.

Por exemplo, nós podemos estar trabalhando em uma funcionalidade que no meio do caminho é cancelada, sendo que nós já tínhamos alterado os arquivos e feito um ou mais commits. Então, aqueles commits não fazem mais sentido no histórico e queremos apagá-los.

Ou, em outra situação comum, você pode estar realizando uma tarefa e outra pessoa inicia a mesma tarefa sem avisar, termina, faz o commit e faz o push. Então, aquele commit que você havia feito também não faz mais sentido e nós queremos apagá-lo.

Temos um comando para fazer isso?

Gabrielle: Sim! Vamos conhecê-lo.

Podemos abrir o nosso arquivo index.html e realizar uma mudança. Na linha 22, nós temos um título H1 "Adivinhe o número secreto":

index.html

<h1>Adivinhe o <span class="container__texto-azul">numero secreto</span></h1>
Copiar código
Vamos apagar essa linha e realizar o commit da maneira que já sabemos: clicando em "Source Control > Stage Changes (ícone de adição)" para adicionar o index.html no commit. Depois, escrevemos uma mensagem de commit no campo de texto logo acima:

Remove título

Depois, clicamos no botão "Commit". Não vamos mandar essa alteração para o GitHub.

E agora, como podemos fazer para reverter esse commit que acabamos de fazer?

Rodrigo: Acabamos de simular a situação em que uma pessoa realizou uma mudança no código, apagando aquele título H1, e fez o commit. Só que ela não sincronizou a atualização e recebemos um pedido para cancelá-la, por exemplo. Mas o commit já está registrado no repositório local dessa pessoa.

Então, podemos rodar um log para visualizar esse commit no histórico, mas terá que ser pelo terminal. Na sequência, aprenderemos a apagar esse commit.

Gabrielle: Vamos fechar a aba do Source Control, abrir um novo terminal e rodar o comando git log.

Rodrigo: Da mesma forma que o revert, se queremos apagar um commit, vamos precisar do ID do commit em questão para identificá-lo.

Gabrielle: Então, vamos copiar o ID do commit "Remove título" que acabamos de fazer:

a3322db2eb6f82162977169f5461fc93b81bfac1
Copiar código
Em seguida, limpamos nosso terminal. O comando para apagar um commit é o git reset --hard junto do ID do commit.

git reset --hard a3322db2eb6f82162977169f5461fc93b81bfac1
Copiar código
Rodrigo: Um detalhe importante: o parâmetro --hard foi colocado porque o comando reset possui algumas opções, alguns modos de realizar esse reset. O parâmetro --hard serve para apagar o commit e também avisei apagar a mudança no código.

No Para Saber Mais desta aula, explicamos outras possibilidades de uso do comando reset.

Gabrielle: Será que funcionou? Vamos rodar o git log no terminal para verificar.

Estranhamente, o commit que tentamos apagar, "Remove título", ainda está presente no histórico. Parece que não funcionou.

Rodrigo: Tem uma pegadinha aí. Na verdade, com o comando reset utilizando a opção --hard, temos que passar o ID do commit, mas não é o ID do commit que queremos resetar, mas sim o ID do comando anterior.

Acabamos copiando o ID do commit "Remove título", mas temos que passar o ID da versão a que queremos retornar. Ou seja, esse comando retorna ao estado do commit indicado pelo ID. Então, seria o ID do commit anterior, "Revert 'remove foto'".

Vamos copiar o ID correto dessa vez e limpar o terminal. Vamos digitar novamente o comando git reset --hard com o ID do commit "Revert 'remove foto'".

git reset --hard 7f69ff8220e093d2c8ad234ceec109a6e794e5f61
Copiar código
Ao dar "Enter", uma mensagem aparece indicando que nosso HEAD agora está no início do ID, que identifica nosso commit.

Vamos rodar novamente o git log. Agora parece que funcionou.

Rodrigo: Aquele último commit, "Remove título", sumiu. Mas será que ele desfez as mudanças no código? Vamos ver se voltou aquele H1 que apagamos.

Gabrielle: Vamos fechar o terminal e expandir o index.html. E pronto, retornou: na linha 22 temos o nosso H1. Deu certo!

Rodrigo: Além do comando revert, que nos permite reverter uma mudança mantendo o commit e criando um novo, temos o comando reset para quando queremos apagar um determinado commit, excluí-lo do histórico porque ele não faz mais sentido.

Nos últimos dois vídeos, nós apresentamos essas duas situações: em uma delas estamos revertendo um commit, na outra estamos apagando um commit. Mas há uma terceira situação possível.

Imagine que não queremos nem apagar nem desfazer, mas alterar um commit. Por exemplo: mudar a mensagem do commit ou incluir um arquivo que esquecemos de adicionar no momento do commit. O Git também nos ajuda com isso.

Gabrielle: Mas antes de falar um pouco mais sobre isso, é importante lembrarmos que o comando reset que acabamos de usar deve ser usado apenas quando tivermos feito esse commit de alteração no nosso repositório local.

Caso já tenhamos subido esse commit, não é tão interessante usar esse comando e alterar o histórico de versões que já está público.

Rodrigo: Essa é mais uma vantagem do Git: nós fazemos os commits e eles só existem localmente até o momento que sincronizamos e enviamos para o GitHub.

No entanto, enquanto o commit está apenas local, as outras pessoas não têm esse commit. Portanto, podemos apagar, desfazer, fazer mudanças. Mas, se já enviamos para o GitHub, não é recomendado apagar um commit, porque isso poderia causar confusão.

Gabrielle: Agora podemos continuar e aprender como realizar uma alteração na mensagem ou algum detalhe de um commit. Vamos lá?!


________________________________________________________________
ranscrição
Rodrigo: Já aprendemos alguns comandos para alterar o histórico, reverter um commit e apagar um commit. No entanto, temos também a terceira situação, onde nós queremos apenas alterar um commit.

Já fizemos a simulação de um novo commit. Vamos rodar um git log no terminal para verificar o que aconteceu.

Lá está o nosso último commit: "Trocando texto do botão avidinhar". Vamos simular essa situação.

A Gabi editou o texto do botão, mudando "chutar" para "adivinhar" e fez o commit. Mas ao digitar a mensagem do commit, houve um pequeno erro. Em vez de "adivinhar", ficou "avidinhar".

Essa é uma situação em que se pensa: Já fiz o commit, e agora? Preciso alterar essa mensagem! Será que vou ter que apagar esse commit e fazer um totalmente novo?

É possível alterar o commit, Gabi?

Gabrielle: Sim! Vamos limpar o terminal primeiro. Podemos fazer isso por meio do comando git commit --amend -m, seguido pela minha mensagem correta, que seria "Trocando botão para adivinhar".

git commit --amend -m "Trocando botao para adivinhar"
Copiar código
Rodrigo: É o próprio comando git commit, como se estivéssemos fazendo um novo commit. Mas não é um novo commit por causa do parâmetro --amend.

Ele indica ao Git que não queremos fazer um novo commit, mas alterar o anterior. Então é só passar o -m, com o texto da mensagem correta.

Gabrielle: Vamos ver se vai dar certo. Após executar o comando acima, temos o retorno de sucesso. Parece que deu certo.

Vamos executar o git log para confirmar se ele realmente alterou o commit anterior em vez de criar um novo commit.

Parece que deu certo! O último commit da lista tem a mensagem "Trocando botao para adivinhar".

Rodrigo: Essa é uma situação comum. Eventualmente digitamos com pressa e acabamos errando a mensagem. Mas não queremos deixar aquela mensagem feia e errada.

Ou a situação pode ter sido a seguinte: você editou seis arquivos, por exemplo, e quando foi fazer o commit, você adicionou cinco e deixou um para trás. E então você fez o commit.

Também é possível fazer esse comando -- amend. Nesse caso você não iria alterar a mensagem, mas precisaria apenas adicionar o arquivo e fazer o commit com o amend.

São situações comuns que, de vez em quando, nos deparamos.

Com isso, aprendemos nessa aula alguns comandos para voltar no tempo, modificar o histórico de versão. Seja para desfazer, apagar ou mesmo alterar um commit.

Na sequência, vamos aprender outros conceitos e recursos dentro do GitHub.

______________________________
esafio 1: Veja todos os commits realizados

Para visualizar todos os commits realizados em um repositório Git, você pode usar o comando git log. Este comando exibe o histórico de commits, mostrando informações como o hash do commit, autor, data, e mensagem do commit. Aqui estão algumas variações do comando git log que podem ser úteis:

Para exibir o histórico completo: git log
Exibir Alterações Detalhadas: git log -p
Exibir Apenas Mensagens de Commit: git log --oneline
Desafio 2: Modificar o Último Commit com git commit --amend:

Faça um commit com algumas alterações no seu código.
Perceba que esqueceu de incluir algumas modificações.
Para adicionar as modificações esquecidas ao último commit, sem criar um novo commit, utilize o comando: git commit --amend
Desafio 3: Reverter Mudanças de um Commit com Git Revert:

Crie um novo arquivo no seu repositório.
Realize um commit adicionando esse novo arquivo.
Para reverter automaticamente as mudanças feitas no último commit sem excluir o histórico: git revert <hash-do-commit>
Se você precisar reverter uma série de commits, pode utilizar o seguinte comando: git revert -n <hash-do-ultimo-commit-a-manter>
Lembre-se que após reverter, é necessário realizar um novo commit para aplicar a reversão ao repositório
Lembre-se de que o git revert é uma maneira segura e não destrutiva de desfazer alterações, pois não reescreve o histórico existente. Ele é particularmente útil em ambientes de trabalho compartilhados, onde reescrever o histórico pode causar problemas para outros colaboradores.

Desafio 4: Apagar um Commit com Git Reset:

Faça uma série de commits com alterações no seu código.
Escolha um commit específico que deseja excluir.
Use para apagar o commit selecionado, desfazendo automaticamente as mudanças no código: git reset --hard <hash-do-ultimo-commit-a-manter>
Se você apenas deseja desfazer commits, mas manter as alterações no diretório de trabalho, você pode usar git reset --soft.
Observação: No cotidiano de trabalho em desenvolvimento, a escolha entre reset e revert deve ser tomada com base nas necessidades específicas do seu projeto e na colaboração com as outras pessoas desenvolvedoras. Se você deseja desfazer alterações em um commit específico sem reescrever o histórico, git revert é uma escolha mais segura. Se você precisa reverter completamente para um estado anterior, git reset pode ser apropriado, mas use-o com cautela, especialmente em branches compartilhadas.

Desafio 5: Sincronize as modificações com o repositório remoto

Execute o comando: git push
Desafio 6: Analise as mensagens de commits realizados e faça as alterações de acordo com as boas práticas:

Para visualizar todo o histórico de commits, execute o comando: git log
Leia a documentação da Conventional Commits para elaborar as mensagens de commits de acordo com as boas práticas
Reescreva os commits utilizando os comandos já aprendidos: git commit –amendou git revert.

---------------------
Milton, parabéns pela dedicação aos estudos! Você mencionou que aprendeu a desfazer, excluir e editar a mensagem dos commits, o que é um ótimo resumo das funcionalidades que abordamos na aula. Além disso, vamos explorar um pouco mais cada um desses comandos para enriquecer seu entendimento. Primeiro, ao usar o comando `git revert`, você reverte as mudanças de um commit específico, criando um novo commit que desfaz as alterações. Isso é útil porque mantém o histórico do projeto intacto, permitindo que você veja o que foi alterado e por quê. Em relação ao `git reset`, ele é um pouco mais drástico, pois remove o commit do histórico. Dependendo da opção que você escolher (como `--soft`, `--mixed` ou `--hard`), ele pode afetar também as mudanças no seu diretório de trabalho. O `--soft` mantém as alterações no staging, enquanto o `--hard` descarta todas as mudanças. Por fim, o comando `git commit --amend` permite que você modifique o último commit, seja para alterar a mensagem ou adicionar novas mudanças. Isso é especialmente útil quando você percebe que esqueceu de incluir algo importante ou cometeu um erro na mensagem. Continue estudando e praticando!

==================================
https://www.alura.com.br/artigos/como-criar-um-readme-para-seu-perfil-github

https://www.alura.com.br/artigos/nova-exigencia-do-git-de-autenticacao-por-token-o-que-e-o-que-devo-fazer