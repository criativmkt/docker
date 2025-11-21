
# Registrador de Despesas - Fullstack (React + NestJS + SQL Server + Docker)

**O que está incluído**
- frontend: React (CRA) com lista, adição e exclusão de despesas
- backend: NestJS (TypeScript) com TypeORM para SQL Server
- infra: Dockerfiles e docker-compose para orquestrar frontend, backend e SQL Server
- roadmap.md com passos de desenvolvimento e testes

**Como rodar (recomendado - via Docker)**
1. Instale Docker Desktop (inclui Docker Compose).
2. Execute no diretório raiz:
```bash
docker compose up --build
```
3. Acesse:
- Frontend: http://localhost:3000
- Backend (API): http://localhost:4000

---

## Execução manual (sem Docker)

> Use esta alternativa apenas se não puder instalar o Docker. Requer que o SQL Server esteja instalado localmente.

### 1. Banco de Dados (SQL Server)
1. Instale o SQL Server (Express ou Developer) e o utilitário `sqlcmd`.  
   - Download SQL Server Express: https://www.microsoft.com/pt-br/sql-server/sql-server-downloads
2. Abra o `sqlcmd` e crie o banco:
```sql
CREATE DATABASE expensesdb;
GO
```

### 2. Backend (NestJS)
```bash
cd backend
copy .env.example .env        # Windows (ou crie manualmente)
npm install
npm run start:dev
```
- Ajuste as variáveis do `.env` se necessário (host, porta, usuário e senha do SQL Server).
- A API ficará disponível em http://localhost:4000.

### 3. Frontend (React)
```bash
cd frontend
npm install
# opcional: crie .env com REACT_APP_API_URL=http://localhost:4000
npm start
```
- A interface abrirá em http://localhost:3000.

### 4. Fluxo de teste manual
- Adicione uma despesa preenchendo todos os campos (Descrição, Valor > 0, Categoria, Data) e clique em **Adicionar Despesa**.
- Verifique se a linha aparece na tabela e se o total é atualizado.
- Clique em **Excluir** para remover e confirmar que o total diminuiu.

