<h1 align="center">Desafio Api Jogos🎲</h1>

## 💻 Descrição do projeto

O projeto tem como objetivo simular um sistema de apostas esportivas, ele deve consumir de uma API contendo os campeonatos, jogos e CPFs dos usuários já cadastrados. Além disso, também deve ser possível consultar na sua API todos os eventos ou filtrar.

---

## 🔨 Funcionalidades

- Realizar apostas: POST `/vendas`;
- Consultar todas as apostas realizadas: GET `/vendas`;
- Consultar os jogos disponíveis: GET `/eventos`;
- Consultar os campeonatos disponíveis: GET `/campeonatos`;
- Consultar informações dos usuários do sistema: GET `/cpf/{cpf}`;
- Filtrar eventos por: GET `/eventos/{id}`, `/eventos/campeonato/{id}` e `/eventos/data/{data}`.

---

## :receipt: Estrutura para realizar o POST '/vendas'

```json
{
  "id_jogo": 354858757161272,
  "opcao_aposta": "1",
  "valor_aposta": 100,
  "cliente_cpf": "368.067.929-79"
}
```
- No primeiro campo será inserido o id do jogo escolhido;
- Posteriormente será necessário informar qual a opção da aposta, nesse caso há três opções: ( 1 : casa | x : empate | 2 : fora);
- No "valor_aposta" será preciso colocar o valor da aposta do usuário, porém cuidado com o limite, pois cada opção e jogo há um limite para o valor de cada aposta;
- E por último o cpf precisa ser válido e está cadastrado no sistema;

**Essa aposta será armazenada da seguinte forma:**
- GET `/vendas`
- Output
```json
[
  {
    "id": 1,
    "id_jogo": 354858324654689,
    "titulo_jogo": "Colômbia x Chile",
    "campeonato": "Copa América - Feminina",
    "data_jogo": "2022-11-24",
    "opcao_aposta": "1",
    "opcao_valor": 1.63,
    "valor_aposta": 100,
    "limite_aposta": 500,
    "cliente_nome": "Lara Nair Santos",
    "cliente_cpf": "368.067.929-79",
    "cliente_nascimento": "20/06/1991",
    "ganho_provavel": 163
  }
]
```


## :clipboard: Consultas GET

#### Consultar Eventos
- GET `/eventos`
- Output
```json
  {
    "id": 354858757161272,
    "titulo": "São Paulo x Flamengo",
    "id_campeonato": 30,
    "data": "2022-12-20",
    "opcoes": [
        { "1": 2.5 }, { "x": 3.1 }, { "2": 1.5 }
    ],
    "limites": [
      { "1": 150 }, { "x": 500 }, { "2": 750 }
    ]
  }
  ```
  
  #### Consultar Evento por 'id'
- GET `/eventos/354858757161272`
- Output
```json
{
  "id": 354858757161273,
  "titulo": "Fluminense x Palmeiras",
  "id_campeonato": 30,
  "data": "2022-12-10",
  "opcoes": [
    { "1": 1.25 }, { "x": 4.5 }, { "2": 3.9}
  ],
  "limites": [
    { "1": 1000 }, { "x": 1000 }, { "2": 1000 }
  ]
}
```

#### Consultar Eventos por Campeonato
- GET `/eventos/campeonato/30`
- Output
```json
{
"id":30,"titulo":"Brasileirão - Serie A"
}
{
"id":354858757161272,
"titulo":"São Paulo x Flamengo",
"id_campeonato":30,
"data":"2022-12-20",
"opcoes":[{"1":2.5},{"x":3.1},{"2":1.5}],
"limites":[{"1":150},{"x":500},{"2":750}]
}
{
"id":354858757161276,
"titulo":"Ceará x Avaí",
"id_campeonato":30,
"data":"2022-08-20",
"opcoes":[{"1":10.14},{"x":2.5},{"2":1.7}],
"limites":[{"1":650},{"x":750},{"2":500}]
}
```

#### Consultar Eventos por Data
-GET `/eventos/data/2022-12-10`
- Output
```json
{
  "id": 354858757161273,
  "titulo": "Fluminense x Palmeiras",
  "id_campeonato": 30,
  "data": "2022-12-10",
  "opcoes": [
    { "1": 1.25 }, { "x": 4.5 }, { "2": 3.9 }
  ],
  "limites": [
    { "1": 1000 }, { "x": 1000 }, { "2": 1000 }
  ]
}
```

#### Consultar Campeonatos
- GET `/campeonatos`
- Output
```json
[
  {
    "id": 30,
    "titulo": "Brasileirão - Serie A"
  },
  {
    "id": 35,
    "titulo": "Copa América - Feminina"
  },
  {
    "id": 36,
    "titulo": "Uruguai - Primeira Divisão"
  }
]
```

#### Consultar Usuário por CPF
- GET `/cpf/36806792979`
- Output
```json
{
  "cpf": "368.067.929-79",
  "nome": "Lara Nair Santos",
  "nascimento": "20/06/1991"
}
```

  
  
