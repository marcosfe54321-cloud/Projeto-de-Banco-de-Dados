# Projeto-de-Banco-de-Dados
Catálogo de Jogos Digitais
Sobre o Projeto
Este sistema foi desenvolvido para gerenciar bibliotecas de jogos, permitindo o controle de progresso, avaliações e coleções personalizadas. A aplicação utiliza o mapeamento objeto-relacional (ORM) para garantir uma comunicação eficiente e segura com o banco de dados PostgreSQL.

1. Configuração do Banco de Dados
A aplicação depende de um servidor PostgreSQL ativo. Siga os passos abaixo:

Criação da Estrutura: No DBeaver, abra e execute o script localizado em /sql/database.sql. Este comando criará as tabelas, constraints (como a nota de 0 a 10) e os gatilhos de automação (como a regra de 1h mínima para finalização).

Variáveis de Ambiente: Crie um arquivo .env na raiz do projeto ou configure as variáveis no seu sistema com o seguinte formato:

Properties
DB_HOST=localhost
DB_PORT=5432
DB_USER=postgres
DB_PASS=sua_senha_aqui
DB_NAME=postgres

2. Como Executar (Passo a Passo)
Instale as Dependências:
Abra o terminal na pasta do projeto e execute:

Bash
pip install sqlalchemy psycopg2-binary python-dotenv
Ajuste a Conexão: No arquivo src/main.py, certifique-se de que a string de conexão está lendo as variáveis acima ou aponte manualmente para o seu banco.

Rode a Aplicação:

Bash
python src/main.py

3. Exemplos de Uso
 Consultas Relacionais (Equivalente a JOIN)
Exemplo de listagem técnica retornada pelo código:

Jogo: Elden Ring | Categoria: RPG | Dono: João Silva

Validação Automática (Integridade)
Tentativa de registrar um jogo finalizado com apenas 0.5h de jogatina:

Erro: Regra de Negócio Violada - Um jogo exige ao menos 1h registrada para ser finalizado.

Explicação dos Componentes Técnicos 
Como configurar o banco:
As variáveis de ambiente são essenciais para que o código seja portátil. Em vez de escrever a senha no código (o que é uma falha de segurança), usamos o arquivo .env. O ORM SQLAlchemy lê essas informações para montar a URL: postgresql://usuario:senha@host:porta/banco.

Comandos de execução
O comando pip install prepara o ambiente instalando o SQLAlchemy (o tradutor entre Python e SQL) e o psycopg2 (o driver de comunicação com o PostgreSQL). O comando python main.py inicia o ciclo de vida da aplicação.

                           EVIDÊNCIAS
 Figura 1: Diagrama Entidade-Relacionamento (DER) gerado no DBeaver, demonstrando a integridade referencial, chaves primárias/estrangeiras e as cardinalidades do sistema.
                           
<img width="1334" height="722" alt="print dbeaver" src="https://github.com/user-attachments/assets/a4bcfba6-f2a1-45b1-83a0-609e33c7c11a" />

Figura 2: Evidência de execução da aplicação Python. O log demonstra a realização de operações CRUD completas e consultas envolvendo relacionamentos entre as entidades do sistema, tudo processado via ORM SQLAlchemy.

<img width="764" height="613" alt="orm acessando" src="https://github.com/user-attachments/assets/5d134a92-44d7-4951-87a9-0ffbf22ddc56" />
