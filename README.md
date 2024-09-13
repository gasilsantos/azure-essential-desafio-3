# azure-essential-desafio-3
criar um banco de dados na azure
# Criando uma Instância de Banco de Dados no Azure

Este guia fornece instruções passo a passo para a criação de uma instância de banco de dados no Microsoft Azure usando o **Azure SQL Database**.

## Pré-requisitos

1. Uma conta no [Azure](https://portal.azure.com/). Se você ainda não tem uma, crie uma conta gratuita.
2. Permissão para criar recursos no **Azure Portal**.

## Passos para criar uma instância de banco de dados no Azure

### 1. Acessar o Portal do Azure

- Navegue até o [Portal do Azure](https://portal.azure.com/).
- Faça login com suas credenciais de conta.

### 2. Criar um Recurso de Banco de Dados

- No painel de controle, clique em **Criar um recurso** no canto superior esquerdo.
- Na barra de pesquisa, digite **SQL Database** e selecione **SQL Database** a partir dos resultados.
- Clique em **Criar**.

### 3. Configurar o Banco de Dados

#### 3.1 Grupo de Recursos

- Selecione um **Grupo de Recursos** existente ou crie um novo. O grupo de recursos é onde todos os seus recursos relacionados ao banco de dados serão armazenados.

#### 3.2 Nome do Banco de Dados

- No campo **Nome do banco de dados**, insira um nome para o seu banco de dados. Por exemplo: `meubancodedados`.

#### 3.3 Servidor

- Se você já tiver um servidor, selecione-o na lista suspensa. Caso contrário:
  - Clique em **Criar novo**.
  - Dê um nome ao servidor.
  - Escolha uma **Região** (idealmente a mais próxima de sua localização).
  - Defina um nome de usuário administrador e senha para o servidor.

#### 3.4 Preço e Desempenho

- Clique em **Configurar banco de dados** para selecionar o modelo de preço que se encaixa no seu orçamento e requisitos de desempenho.
  - **Nível Básico**: Bom para pequenos aplicativos ou para desenvolvimento/testes.
  - **Nível Standard ou Premium**: Indicado para produção com necessidades de alta disponibilidade e desempenho.
  
- Após selecionar o nível desejado, clique em **Aplicar**.

#### 3.5 Opções Adicionais

- Escolha a política de backup que melhor atenda às suas necessidades, se for aplicável.
- Clique em **Revisar + Criar**.

### 4. Revisar e Criar

- Revise todas as configurações da instância de banco de dados.
- Clique em **Criar** para iniciar o provisionamento do banco de dados.

### 5. Acessar o Banco de Dados

- Após a criação ser concluída (pode levar alguns minutos), navegue até o **Grupo de Recursos** onde o banco de dados foi criado.
- Selecione o banco de dados.
- No painel esquerdo, clique em **Query Editor (preview)** para acessar diretamente o banco de dados ou configure um cliente SQL externo como **Azure Data Studio** ou **SQL Server Management Studio (SSMS)** para gerenciar sua instância.

### 6. Configurar as Regras de Firewall

- Para acessar o banco de dados de fora do Azure, você precisa configurar as regras de firewall:
  - Navegue até o servidor criado.
  - No painel esquerdo, clique em **Configurações > Regras de firewall e redes virtuais**.
  - Adicione o seu **Endereço IP público** ou **Faixa de IPs** que terão acesso ao servidor e ao banco de dados.
  - Clique em **Salvar**.
![DALL·E-2024-09-12-21 00 34-A-modern-and-sleek-illustration-representing-databases](https://github.com/user-attachments/assets/b5fb55ff-44b9-4689-85e0-617a6cafa764)

### 7. Conectando-se ao Banco de Dados

- Use o cliente SQL ou aplicativos para se conectar ao banco de dados usando o nome do servidor, nome do banco de dados, nome de usuário administrador e senha.

Exemplo de string de conexão (para C#):
```csharp
Server=tcp:<seu-servidor>.database.windows.net,1433;Initial Catalog=<seu-banco-de-dados>;Persist Security Info=False;User ID=<seu-usuario>;Password=<sua-senha>;MultipleActiveResultSets=False;Encrypt=True;TrustServerCertificate=False;Connection Timeout=30;
