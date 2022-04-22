# Curso de Git e Github:cat:

## Git & Github

Entendendo o que é e o que pode fornecer o Git e o Github em conjunto:	

1. Controle de versão;

2. Armazenamento em nuvem;

3. Trabalho em equipe;

4. Melhora do código;

5. Reconhecimento pela comunidade Dev.

   

## Git x Github

​	As aplicações complexas não são feitas com apenas um Desenvolvedor e sim de forma colaborativa podendo uma equipe se distribuir pelo mundo inteiro permitindo o *Git* o monitoramento,  controle de diferentes versões contidas dentro de suas maquinas de forma segura, atualização e compartilhamento da ultima versão a todos da equipe pela guarda do codigo da aplicação no *Github* na nuvem.

## Comando Basicos no CLI

1. Mudar de pastas

2. Listar as pastas

3. Criar pastas/arquivos

4. Deletar pastas/arquivos

   

   Windows (*terminal shell*) /  Unix (*terminal bash*)

   * cd / cd (navegar pelos diretórios/pastas )

     cd / (vai para a raiz / base do sistema)

     cd /*nome do diretório* (navega para pasta)

     cd .. (retrocede uma pasta acima ou varias cd ../ ../)

   * dir / ls (listar conteúdo dentro dos diretórios/pastas)

   * mkdir / mkdir (criar uma pasta)

   * del ou rmdir /  rm -rf (deletar uma pasta ou repositórios de forma recursiva)

   * cls / clear ou Ctrl +L (limpar o terminal)

   * TAB (autocompletar)

   * echo (printa strings no terminal)

     echo *menssagem*> *arquivo.txt* (redirecinador de fluxo do echo e criação de arquivo caso o sistema operacinal já não tenha criado)

     ## 

## Instalação do Git no Ubuntu pelo Terminal

```
# add-apt-repository ppa:git-core/ppa -y  `# apt update; apt install git 
```



## Entendo como o Git funciona

1. SHA1
2. Objetos fundamentais
3. Sistema distribuído
4. Segurança

​	A sigla SHA signnifica Secure Hash Algorithm (Algoritimo de Hash Seguro), é um conjunto de funções hash criptográficas projetadas pela NSA (Agência de de Segurança Nacional dos EUA).

​	A saída da encriptação gera um conjunto de caracteres indenficador de 40 dígitos único e qualquer mudança no arquivo o SHA criará um conjunto diferente de caracteres, mas se a alteração for retirada e o arquivo voltar ao original o SHA vai gerar os mesmos caracteres inicial antes da mudança.

​	É uma forma curta de representar um arquivo

**toni@toni:~/workspace$ echo 'Olá mundo' | openssl sha1
(stdin)= 55096f0bbdb89e479ebd03c8bcb39f88f4269214**

## Objetos internos do GIT

1. BLOBS

2. TREES

3. COMMITS

   

**toni@toni:~/workspace$ echo 'conteudo' | git hash-object --stdin
fc31e91b26cf85a55e072476de7f263c89260eb1 (usando função do git)
toni@toni:~/workspace$ echo -e 'conteudo' | openssl sha1
(stdin)= 65b0d0dda479cc03cce59528e28961e498155f5c**

![](/home/toni/Imagens/Screenshot from 2022-04-22 01-06-21.png)

​	Os objetos especificos do git possui meta dados e geram SHA diferentes do openssl

​	Agora seram passados os metadados e a chave será igual a primeira

**toni@toni:~/workspace$ echo 'conteudo' | git hash-object --stdin
fc31e91b26cf85a55e072476de7f263c89260eb1
toni@toni:~/workspace$ echo -e 'conteudo' | openssl sha1
(stdin)= 65b0d0dda479cc03cce59528e28961e498155f5c
toni@toni:~/workspace$ echo -e 'blob 9\0conteudo' | openssl sha1
(stdin)= fc31e91b26cf85a55e072476de7f263c89260eb1**

![](/home/toni/Imagens/Screenshot from 2022-04-22 01-15-51.png)

​	A Tree armazenam e apontam para tipos de Blob  e outras Tree diferentes e tambem contem metas dados e guarda o nome do arquivo

​	Qualquer alteração irá alterar todos os SHA

​	![](/home/toni/Imagens/Screenshot from 2022-04-22 01-21-14.png)

​	Por fim o objeto mais importante de todos que ira juntar tudo e dar sentido as alteraçoes que estaram sendo feitas será o commite que alem de conter tree e blob tambem contem parente (o commit anterior), menssagem, registro de data e hora

![](/home/toni/Imagens/Screenshot from 2022-04-22 01-23-20.png)

​	Podendo também ser colocada uma messagem para entendimento onde foi a mudança. Se alterar o sha do blob será tambem alterado o sha da tree que por sua vez será alterado o sha do commit, fiicando então, uma linha do tempo de todas as alterações e o autor do commit garantindo segurança e confiabilidade.

![](/home/toni/Imagens/Screenshot from 2022-04-22 01-29-00.png)

​	Ele se apresenta como um sistema distribuido seguro porque o codigo se que encontra no host na nuvem representa a vesão mais atualizada, mas todos os integrantes da equipe tambem possuem versões confiaveis em suas maquinas.

## Primeiros comandos com  GIT

1. Iniciar o GIT
2. Iniciar o vercionamento
3. Criar um commit
   * git init (inicia o repositorio do git)
   * git add (para mover arquivos)
   * git commit

## Criando um repositorio

Criar uma pasta podendo ser o nome **workspace** (mkdir)

Cria uma pasta dentro da workspace (mkdir  livro-receitas)

Dentro da passta livro-receitas digitar **git init**

![cd](/home/toni/Imagens/Screenshot from 2022-04-22 09-48-48.png)

![](/home/toni/Imagens/Screenshot from 2022-04-22 09-59-06.png)

## Utilizando o editor de testo Markdown

![](/home/toni/Imagens/Screenshot from 2022-04-22 10-12-55.png)

commitando o qrquivo criado

* git add *

* git commit -m "Commit inicial"

![](/home/toni/Imagens/Screenshot from 2022-04-22 10-20-35.png)

## Ciclo de vida dos arquivos

* Git init cria um repositório no diretorio

![](/home/toni/Imagens/Screenshot from 2022-04-22 10-25-09.png)

1. Dentro do tracked estão os arquivos que podem ser rastreado pelo git (ummodifided, modified e staged)

2. Untracked estão os arquivos que o git ainda não tem consciencia

3. Ummodified são os arquivos conhecido pelo git, mas ainda não foram modificados

4. Modified são os arquivos que o git tem conhecimento e foram modificados

5. Staged é um conceito chave, ali  é uma area onde se encontram os arquivos que sofreram **git add** e estão preparados para posteriomente sofrerem **commit** (tira uma foto e criptografa  e vam para umodified populando o repositorio local)

   

![](/home/toni/Imagens/Screenshot from 2022-04-22 10-42-03.png)

​	O repositorio remoto esta guardado no servidor

​	Da area de trabalho na sua maquina o arquivo modificado segue para a area staged pelo comando git add e sofrendo commit vai para o repositorio local e ainda não foi para o reservatorio remoto.

​	O **git status** monitora a posição do arquivo

​	Cria uma pasta receita e mover o arquivo salada-tomate.md para ela

![](/home/toni/Imagens/Screenshot from 2022-04-22 11-05-09.png)

![](/home/toni/Imagens/Screenshot from 2022-04-22 11-08-25.png)

![](/home/toni/Imagens/Screenshot from 2022-04-22 11-14-05.png)

![](/home/toni/Imagens/Screenshot from 2022-04-22 11-18-47.png)

![](/home/toni/Imagens/Screenshot from 2022-04-22 11-35-29.png)