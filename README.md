# README - Javadoc

Este documento descreve o funcionamento do pacote `login`, responsável pela autenticação de usuários em um banco de dados MySQL.

---

## 1. Descrição Geral

O pacote **login** contém a classe `User`, que gerencia o processo de autenticação de usuários. Ele se conecta a um banco de dados MySQL e valida se as credenciais fornecidas (login e senha) existem.

---

## 2. Importações Necessárias

As seguintes classes Java são utilizadas para o funcionamento do pacote:

- `java.sql.Connection`
- `java.sql.DriverManager`
- `java.sql.ResultSet`
- `java.sql.Statement`

---

## 3. Classe `User`

### 3.1 Função
A classe `User` implementa o sistema de login para autenticação de usuários no banco de dados.

### 3.2 Autor e Versão
- **Autor:** João Vitor Amaral Franzoni  
- **Versão:** 1.0

### 3.3 Atributos
- **`nome`**: Armazena o nome do usuário retornado pela consulta SQL após autenticação bem-sucedida.
- **`result`**: Indica o resultado da verificação das credenciais (true para credenciais válidas, false para inválidas).

---

## 4. Métodos

### 4.1 `conectarBD()`
**Descrição:**  
Estabelece uma conexão com o banco de dados MySQL.

- **Retorno:**  
  - Um objeto representando a conexão do banco de dados, caso a conexão seja bem-sucedida.
  - `null`, caso a conexão falhe.

### 4.2 `verificarUsuario(String login, String senha)`
**Descrição:**  
Verifica se o login e a senha fornecidos estão cadastrados no banco de dados.

- **Parâmetros:**  
  - `login`: O login do usuário a ser autenticado.  
  - `senha`: A senha correspondente ao login.

- **Retorno:**  
  - Define `result = true` se as credenciais forem válidas.  
  - Define `result = false` caso contrário.

---

## 5. Considerações e Melhorias Sugeridas

### 5.1 Tratamento de Exceções
O código atual captura exceções, mas não fornece mensagens detalhadas, dificultando o diagnóstico de falhas.

**Recomendação:**  
Adicionar logs ou mensagens explicativas nos blocos `catch`:
```java
catch (Exception e) {
    System.err.println("Erro ao conectar ao banco de dados: " + e.getMessage());
    e.printStackTrace();
}
