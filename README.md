# Nest do Zero

Projeto de exemplo usando **NestJS + Prisma** para demonstrar uma aplicação simples com CRUD mínimo.

---

## Tecnologias

- 🟣 Node.js / TypeScript  
- 🚀 NestJS (framework backend)  
- 💾 Prisma ORM  
- 🗃️ SQLite (como banco de dados leve para exemplo)  

---

## Estrutura do Projeto

```bash
    src/
    ├── database
    ├── dtos
    ├── repositories
    ├── app.controller.ts
    ├── app.module.ts
    ├── database/
    │ └── prisma.service.ts
    └── ...
    prisma/
    └── schema.prisma
    generated/
    └── prisma/ ← diretório onde o client Prisma é gerado
    .env
    README.md
    package.json
    tsconfig.json
```


- O `schema.prisma` define o modelo `RocketTeamMember` com campos `id`, `name` e `function`.  
- O `PrismaService` estende o `PrismaClient` gerado.  
- O `AppController` demonstra como criar um membro via endpoint.  

---

## Instalação e Execução

1. Clone este repositório:

   ```bash
   git clone https://github.com/gameplaybiel/nest_do_zero.git
   cd nest_do_zero

2. Instale as dependências:
```bash
npm install
```

3. Configure sua variável DATABASE_URL no arquivo .env, por exemplo:
```bash
DATABASE_URL="file:./dev.db"
```

4. Gere o client Prisma:
```bash
npx prisma generate
```

5. (Opcional) Rode migrações, se houver:
```bash
npx prisma migrate dev --name init
```

6. Inicie a aplicação:
```bash
npm run start:dev
```

A aplicação vai subir e escutar (por padrão) a porta 3000.

---
## Endpoints de Exemplo

POST /app/hello — cria um novo membro no banco.

Body JSON esperado:
```json
{
  "name": "Gabriel Capitao",
  "function": "Alcançar coisas no alto"
}
```

Retorna o membro criado com id, name e function.

Você pode depois criar outros endpoints (GET, PUT, DELETE) para completar o CRUD.

## Boas Práticas / Melhorias Futuras
- Usar DTOs com validação (ex: class-validator) para garantir que name e function não venham vazios.
- Separar em módulos: por ex. team module com team.controller, team.service, team.dto etc.
- Adicionar tratamento de erros mais robusto (ex: duplicidade, campos inválidos).
- Usar migrations para evoluir o esquema do banco de dados.
- Testes unitários/integrados com Jest.

## Contribuições
Fique à vontade para fazer um fork, abrir issues ou pull requests. Qualquer sugestão para melhorias será bem-vinda!

## Licença

Este projeto está sob a licença MIT — sinta-se livre para usar, modificar ou redistribuir.