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
