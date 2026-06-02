Banco de dados - Atividade
Stored-Procedures
Parte 1: Instalação e Inicialização no Codespaces
Como o Codespaces roda em containers sem systemd, use os comandos abaixo no terminal:
1. Atualize os pacotes e instale o servidor:
terminal
```
sudo apt update && sudo apt install -y mysql-server
```
2. Inicie o serviço do MySQL:
terminal
sudo service mysql start
3. Acesse o console do MySQL como administrador:
terminal
sudo mysql -u root

Parte 2: Criação do Banco e da Tabela
Dentro do console do MySQL (onde o prompt muda para mysql>), execute os comandos
abaixo:
1. Crie o banco de dados:
sql
CREATE DATABASE escola;
2. Selecione o banco de dados criado:
sql
USE escola;
3. Crie a tabela aluno:
sql
CREATE TABLE aluno (
id_aluno INT AUTO_INCREMENT PRIMARY KEY,
nome VARCHAR(100) NOT NULL,
nota DECIMAL(4,2) NOT NULL
);

Parte 3: Criação da Stored Procedure
Ainda dentro do console do MySQL, use o código abaixo. Mudamos o delimitador para // para
que o MySQL não confunda os pontos e vírgulas da Procedure com o fim do comando.
1. Cole o bloco de código da Procedure:

sql
DELIMITER //
CREATE PROCEDURE InserirAluno(
IN p_nome VARCHAR(100),
IN p_nota DECIMAL(4,2)
)
BEGIN
INSERT INTO aluno (nome, nota) VALUES (p_nome, p_nota);
END //
DELIMITER ;

Parte 4: Como Testar a Procedure
1. Execute a Procedure para inserir um aluno de teste:
sql
CALL InserirAluno('Carlos Silva', 8.5); --- insira aqui o NOME DE
TODOS OS ALUNOS DA SALA seu nome
uma nota ...
Use o código com cuidado.
2. Consulte a tabela para verificar se o registro foi salvo:
sql
SELECT * FROM aluno;

PARA ENTREGAR A ATIVIDADE VC DEVE
FAZER UM PRINT OU CAPTURA DA TELA
DOS REGISTRO INSERIDOS E POSTAR
NESSE CLASSROOM ....