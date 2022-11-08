<h1 align="center">Desafio Api Jogos🎲</h1>

## 💻 Descrição do projeto

O projeto tem como objetivo simular um sistema de apostas esportivas, ele deve consumir de uma API contendo os campeonatos, jogos e CPFs dos usuários já cadastrados. Além disso, também deve ser possível consultar na sua API todos os eventos ou filtrar.

---

## 🔨 Funcionalidades:

- Realizar apostas: POST `/venda`;
- Consultar todas as apostas realizadas: GET `/venda`;
- Consultar os jogos disponíveis: GET `/eventos`;
- Consultar os campeonatos disponíveis: GET `/campeonatos`;
- Consultar informações dos usuários do sistema: GET `/cpf/{cpf}`;
- Filtrar eventos por: GET `/eventos/{id}`, `/eventos/{campeonato}` e `/eventos/{data}`.
