# curso-alura-maven
Curso de Maven: Gerenciamento de dependências e build de aplicações Java

## Módulo 01 - Conhecendo o Maven
### Aula 01.01 - Apresentação
- Maven é um gerenciador de dependências

### Aula 01.02 - Projeto inicial

### Aula 01.03 - Build e dependências em uma aplicação Java
- `Apache Ant`: anteriormente era utilizado para tratar do processo de build de uma aplicação.
- `Apache Ivy`: anteriormente era utilizado para gerenciar as dependências do projeto.
- O `Maven` realiza o processo de build e gerência das dependências

### Aula 01.04 - Ferramentas de build
Quais as principais vantagens de se utilizar o Maven em uma aplicação Java?  
`R:` Gerenciamento de dependências e Automatização do build

### Aula 01.05 - Instalação do Maven
- [https://maven.apache.org/install.html](https://maven.apache.org/install.html)
- para configurar no path do sistema adicione o conteúdo abaixo no arquivo `~/.profile` ou `/etc/profile`:
```bash
export M3_HOME=/opt/maven  #ou diretório do maven
export PATH=$M3_HOME/bin:$PATH
```
- Também pode ser utilizado dentro de sua IDE (Eclipse ou Intellij).

### Aula 01.06 - Utilização do Maven
Quais as principais maneiras de se utilizar o Maven?
- Pelo prompt de comandos
- Pela integração com a IDE

### Aula 01.07 - Faça como eu fiz

### Aula 01.08 - O que aprendemos?
- As dificuldades de se realizar manualmente o build de uma aplicação Java;
- As dificuldades de se gerenciar manualmente as dependências de uma aplicação Java;
- O que é o Maven;
- Como instalar e executar o Maven.

## Módulo 02 - Projetos com Maven
### Aula 02.01 - Criando um projeto com Maven
- `File > New > Maven Project`, na janela que abrir selecione a opção `Criar projeto simples` e `Use o Workspace Padrão` e `Next`. Na próxima tela preencha o campo Group Id  com a identificação da empresa (Ex: br.com.alura), Artifact Id com a identificação do projeto (nome do projeto) e `Finish`.

### Aula 02.02 - GroupId de um projeto com Maven
O GroupId é utilizado para identificar, unicamente, a organização ao qual o projeto pertence. GroupId é como um pacote do Java, tendo como objetivo identificar a organização ao qual o projeto pertence.

### Aula 02.03 - Estrutura de um projeto com Maven
- `src/main/java`: contém os códigos java (classes, enums e interfaces).
- `src/main/resources`: arquivos de configuração do projeto (Ex: persistence.xml, application.properties e messages.properties).
- `src/test/java`: arquivos de testes automatizados.
- `src/test/resources`:
- `pom.xml`: arquivo com as configurações, build e dependências do projeto.

### Aula 02.04 - Source folders
Que tipos de arquivos normalmente encontramos no diretório `src/main/resources`?  
`R:` Arquivos de configuração

### Aula 02.05 - Adicionando Maven a um projeto existente
- botão direito do mouse > `Configure` > `Convert to maven project`
- Na janela que abrir configure o `GroupId`, `ArtifactId`, `Version`, `Packaging` > `Finish`.
- No arquivo `pom.xml` estará configurado, dentro da tag `<build>`, a estrutura atual do projeto.
- Para atualizar a estrutura do projeto para maven realize os passos abaixo:
  - Botão direito do mouse no projeto > `Build Path` > `Configure Build Path...`
  - Na aba `Source`, remova os diretórios e `Apply`. Clique em `Add new Folder` para criar os diretórios: `src/main/java`, `src/main/resources`, `src/test/java` e `src/test/resources`. No diretório `src/test/java`, altere a opção `Contains test resource` para yes e na opção `Output folder` altere para `Specific output folder` apontando para `target/test-classes` . Repita o mesmo para o diretório `src/test/resources`. 
  - Ainda na aba `Source` devemos alterar, nos diretórios 
`src/main/resources` e `src/test/resources`, a opção `Exclude` e adicionar, na janela que abrir, em `Exclusion Patterns` > `Add` com `**` > `OK`. Agora clicar em `Apply` e `Apply and Close`.
  - Agora basta mover as classes e arquivos de configuração do diretório src para as devidas classes. Também mova a pasta `Webcontent` para `src/main` e renomei-a para `webapp`.
  - Removemos as configurações da estrutura antiga do projeto no arquivo `pom.xml`. Por exemplo, as tags `sourceDirectory`, `testRourceDirectory`, `resource`. também devemos remover a tag `configuration`, dentro do plugin maven-war-plugin, que contém o diretório antigo com os arquivos web, `WebContent`.
  - Botão direito do mouse no projeto > `Maven` > `Update Project` > `OK` para atualizar o projeto.
  - faltando agora, somente, adicionar as dependências no arquivo `pom.xml` e removermos o diretório `src/main/webapp/WEB-INF/lib` com os jars do proojeto.

  > Obs: caso a opção "Output folder", no build path do projeto, não aparecer verifique a caixa de seleção da opção `Allow output folders for source folders` estar desmarcada, na aba Source do Java Build Path. Fonte: [Fórum da Alura](https://cursos.alura.com.br/forum/topico-problema-com-a-conversao-de-projeto-web-para-projeto-maven-146619)

### Aula 02.06 - Faça como eu fiz

### Aula 02.07 - O que aprendemos?
- A criar uma aplicação com Maven;
- A entender a estrutura de diretórios de uma aplicação com Maven;
- A migrar uma aplicação para o Maven.

## Módulo 03 - Dependências no Maven
### Aula 03.01 - Gerenciando dependências no Maven
- Exemplo de dependência no arquivo `pom.xml`:
```xml
	<dependencies>
		<dependency>
			<groupId>junit</groupId>
			<artifactId>junit</artifactId>
			<version>4.12</version>
			<scope>test</scope>
		</dependency>
	</dependencies>
```
