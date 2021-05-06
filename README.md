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

### Aula 03.02 - Pesquisando por dependências
- [Mvn Repository](https://mvnrepository.com/)

### Aula 03.03 - Repositório central
Por padrão, de onde o Maven baixa as dependências de uma aplicação?  
`R:` Do repositório central do próprio Maven. O Maven possui um repositório central de dependências.

### Aula 03.04 - Alterando o repositório remoto de dependências
- O Maven procura a dependências no cache local, depois o repositório configurado no pom.xml e por último no Repositório Maven da Internet.
Exemplo de arquivo `pom.xml` com repository customizado:
```xml
	<repositories>
		<repository>
			<id>spring-repo</id>
			<url>https://repo.spring.io/releases</url>
		</repository>
	</repositories>
```
### Aula 03.05 - Repositórios remotos
Por qual motivo precisariámos adicionar algum repositório remoto?  
`R:` Para baixar dependências que não estão no repositório central do Maven. Pode acontecer de alguma dependência da aplicação ser disponibilizada apenas em outros repositórios remotos.

### Aula 03.06 - Faça como eu fiz

### Aula 03.07 - O que aprendemos?
- A como declarar as dependências de uma aplicação;
- A como pesquisar por dependências no repositório central do Maven;
- A como configurar outros repositórios remotos.

## Módulo 04 - Build no Maven
### Aula 04.01 - Projeto da aula anterior

### Aula 04.02 - Processo de build no Maven
- `mvn compile`: compila o projeto.
- `mvn clean`: limpa o diretório de build.
- `mvn test`: executa os testes.
- exemplo de configuração de versão de java no `pom.xml`:
```xml
<build>
  <plugins>
    <plugin>
      <artifactId>maven-compiler-plugin</artifactId>
      <configuration>
        <source>8</source>
        <target>8</target>
      </configuration>
    </plugin>
  </plugins>
</build>
```

### Aula 04.03 - Goals do Maven
Qual o objetivo do goal test (`mvn test`)?  
`R:` Executar os testes automatizados da aplicação. O comando mvn test executa os testes automatizados da aplicação, apresentando ao final um relatório.

### Aula 04.04 - Gerando o artefato do build
- `mvn package`: gera o pacote da aplicação (jar/war).
- `mvn install`: adiciona o seu projeto no repositório local do maven (`.m2/repository`).
- `mvn deploy`: adiciona o seu projeto no repositório remoto, caso esteja configurado.
- para definir o no do pacote devemos adicionar a tag `<finalName>loja</finalName>` no arquivo `pom.xml`, dentro da tag build.

### Aula 04.05 - Empacotando a aplicação
Onde podemos encontrar, por padrão, o artefato gerado pelo Maven?  
`R:` No diretório target da aplicação.

### Aula 04.06 - Faça como eu fiz

### Aula 04.07 - O que aprendemos?
- A realizar o build da aplicação com Maven;
- A utilizar o comando `mvn nome-do-goal` para realizar o build;
- Alguns goals do Maven, como `compile`, `test` e `package`;
- A personalizar o artefato de build gerado pelo Maven.

## Módulo 05 - Outros recursos
### Aula 05.01 - Projeto da aula anterior

### Aula 05.02 - Plugins
- [https://maven.apache.org/plugins/](https://maven.apache.org/plugins/)
- Exemplo de adição do plugin jacoco no `pom.xml`:
```xml
<plugin>
  <groupId>org.jacoco</groupId>
  <artifactId>jacoco-maven-plugin</artifactId>
  <version>0.8.2</version>
  <executions>
    <execution>
            <goals>
                <goal>prepare-agent</goal>
            </goals>
    </execution>
        <execution>
            <id>report</id>
            <phase>test</phase>
            <goals>
                <goal>report</goal>
            </goals>
        </execution>
  </executions>
</plugin>
```
- para gerar os relatório execute: `mvn clean test`
- para acessar o relatório acesse `target/site/jacoco/br.com.alura.loja/index.html`

### Aula 05.03 - Plugins do Maven
Qual o objetivo de se utilizar plugins?  
`R:` Adicionar novas funcionalidades ao Maven. Plugins servem para extender os comportamentos do Maven.

### Aula 05.04 - Proxy
- Adicione ou atualizae o código abaixo no arquivo `/home/{username}/.m2/settings.xml` e altere conforme as suas configurações:
```xml
<settings xmlns="https://maven.apache.org/SETTINGS/1.0.0"
      xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance"
      xsi:schemaLocation="https://maven.apache.org/SETTINGS/1.0.0
                          https://maven.apache.org/xsd/settings-1.0.0.xsd">
  <proxies>
    <proxy>
      <id>meu-proxy</id>
      <active>true</active>
      <protocol>http</protocol>
      <host>http://192.168.0.1</host>
      <port>3128</port>
      <username>username</username>
      <password>password</password>
    </proxy>
  </proxies>
</settings>
```

### Aula 05.05 - Módulos
- O java 9 já suporta o uso de módulos
- O maven também suporta o uso de módulos
- Exemplo de `pom.xml` do projeto principal:
```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
	<modelVersion>4.0.0</modelVersion>
	<groupId>br.com.caelum.fj91</groupId>
	<artifactId>rh</artifactId>
	<version>1.0</version>
	<packaging>pom</packaging>

	<properties>
		<project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
		<project.reporting.outputEncoding>UTF-8</project.reporting.outputEncoding>
		<java.version>1.8</java.version>
		<maven.compiler.target>1.8</maven.compiler.target>
        <maven.compiler.source>1.8</maven.compiler.source>
	</properties>

	<dependencies>
		<dependency>
			<groupId>junit</groupId>
			<artifactId>junit</artifactId>
			<version>4.12</version>
			<scope>test</scope>
		</dependency>

		<dependency>
			<groupId>org.mockito</groupId>
			<artifactId>mockito-all</artifactId>
			<version>1.10.19</version>
			<scope>test</scope>
		</dependency>
	</dependencies>

	<modules>
		<module>rh-domain</module>
		<module>rh-web</module>
		<module>rh-persistencia</module>
	</modules>

</project>
```
- Exemplo de `pom.xml` do módulo rh-domain:
```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
	<modelVersion>4.0.0</modelVersion>
	<artifactId>rh-domain</artifactId>
	
	<parent>
		<groupId>br.com.caelum.fj91</groupId>
		<artifactId>rh</artifactId>
		<version>1.0</version>
	</parent>
	
</project>
```
- [Projeto de exemplo com uso de módulo](https://github.com/forks-projects/fj91-clean-architecture)

### Aula 05.06 - Modularização de projetos
Como o Maven identifica os módulos de um projeto?  
`R:` Pela tag `<modules>` adicionada no `pom.xml`.

### Aula 05.07 - Faça como eu fiz

### Aula 05.08 - O que aprendemos?
- A utilizar plugins do Maven;
- A como configurar um proxy no Maven;
- A como configurar uma aplicação modularizada no Maven.

### Aula 05.09 - Conclusão
