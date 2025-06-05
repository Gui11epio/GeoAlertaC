# 🌍 GeoAlertaC

API desenvolvida em .NET com foco na coleta e análise de dados climáticos para identificar riscos de deslizamento em determinadas regiões. O sistema recebe dados de sensores/meteo, armazena informações de usuários e endereços, e calcula o risco com base em regras predefinidas.

---

## 👥 Nome e RM dos Integrantes

- Guilherme Camasmie Laiber de Jesus – RM554894

- Fernando Fernandes Prado – RM557982

- Pedro Manzo Yokoo – RM556115


## 🛠️ Tecnologias Utilizadas

- ASP.NET Core
- C#
- Entity Framework Core
- Swagger (OpenAPI) para documentação
- Visual Studio 2022
- Oracle DataBase
- AutoMapper
- Migrations
- DataAnnotations

## 🧭 Visão Geral do Funcionamento

### Fluxo da API (.NET)
```mermaid
flowchart TD
    Frontend -->|Requisições HTTP| Controllers
    Controllers -->|Validação e Mapeamento| Services
    Services -->|Regras de Negócio| Repositories
    Services -->|Risco calculado| AlertaService
    Repositories -->|Acesso a dados| BancoDeDados[(Oracle DB)]
    AlertaService -->|Criação de alertas| BancoDeDados
```


# 🚀 Como Executar o Projeto

## Execução Local

1. **Clone o repositório ou baixe ele**
    ```bash
    https://github.com/Gui11epio/GeoAlertaC.git
    ```

2. **Vá até "lauchSettings.json"**
   
   ![image](https://github.com/user-attachments/assets/3dfea516-6dd4-4d77-8518-3e01ec3f6d5b)


3. **Coloque suas informações do Banco de Dados Oracle**

   ![image](https://github.com/user-attachments/assets/901e8090-a7ef-41b1-b1b1-54c9bdd546eb)


4. **Na terminal do projeto coloque as mesmas informações da Oracle**
    ```bash
    $env:CONEXAO_GS = "User Id=xxxxxxx;Password=xxxxxxx;Data Source=oracle.fiap.com.b:1521/ORCL";
    ```

5. **Ainda na terminal, rode este comando para criar as tabelas em seu banco de dados:**
     ```bash
     dotnet ef database update
     ```
6. **De um Build no seu projeto e o Swagger abrirá sozinho**

