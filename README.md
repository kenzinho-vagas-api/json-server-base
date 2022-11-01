<h1 align="center">
  Kenzinho Vagas - API
</h1>

<p align = "center">
  http://localhost:3001 🡪 Essa base irá mudar assim que colocarmos no Heroku.
</p>

<p align="center">
  <a href="#endpoints">Endpoints</a>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</p>

## **Endpoints**

## Rotas que não precisam de autenticação

<h2 align ='center'> Cadastro (POST) </h2>

URL: http://localhost:3001/signup

```json
body: {
	"name": "Admin",
	"email": "admin@mail.com",
	"password": "12345",
	"isAdmin": true
}

O body do admin é bem mais simplificado porque ele não precisa dizer cargo, especialidade....

Resposta: {
	"accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6ImFkbWluQG1haWwuY29tIiwiaWF0IjoxNjY3MzExODA3LCJleHAiOjE2NjczMTU0MDcsInN1YiI6IjEifQ.f_abmWVQVrQw_yJTq8I_8RfGCS0_0cIlp5QyVv3Ru_E",
	"user": {
		"email": "admin@mail.com",
		"name": "Admin",
		"isAdmin": true,
		"id": 1
	}
}
```

<h2 align ='center'> Login (POST) </h2>

URL: http://localhost:3001/login

```json
body: {
	"email": "admin@mail.com",
	"password": "12345"
} 

Resposta: {
	"accessToken":       "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6ImFkbWluQG1haWwuY29tIiwiaWF0IjoxNjY3MzE2MjU2LCJleHAiOjE2NjczMTk4NTYsInN1YiI6IjEifQ.hLGHdluCoL1Cz9EwGxssfTsK3wZ1WuZ1rtvVa__shd4",
	"user": {
		"email": "admin@mail.com",
		"name": "Admin",
		"isAdmin": true,
		"id": 1
	}
}
```

<h2 align ='center'> Ver vagas criadas (GET) </h2>

URL: http://localhost:3001/companyJobs

## Rotas que precisam de autenticação

<h2 align ='center'> Criar vaga (POST) </h2>

URL: http://localhost:3001/users/1/companyJobs
O número 1 é referente ao id do admin

```json
body: {
"company_name": "Teste Empresas 03",
	"specialty": "Back-end",
	"salary": "15000",
	"kind_of_work": "Remoto",
	"tech": ["React", "TypeScript", "Node.js"],
	"level": "Júnior",
	"jobURL": "",
"description": "Vaga destinada a júniors (2 a 4 anos de experiência), além disso é imprescíndivel que o programador tenha experiência com Node.js e TypeScript"
}

Resposta: {
	"company_name": "Teste Empresas 03",
	"specialty": "Back-end",
	"salary": "15000",
	"kind_of_work": "Remoto",
	"tech": [
		"React",
		"TypeScript",
		"Node.js"
	],
	"level": "Júnior",
	"jobURL": "",
	"description": "Vaga destinada a júniors (2 a 4 anos de experiência), além disso é imprescíndivel que o programador tenha experiência com Node.js e TypeScript",
	"userId": "1", (id de quem criou)
	"id": 3 (id da empresa criada)
  }
}
```

<h2 align ='center'> Editar vaga (PATCH) </h2>

URL: http://localhost:3001/companyJobs/1 
O número 1 é referente ao id da empresa

```json
body: 	{
	"salary": "20000",
	"kind_of_work": "Presencial",
	"level": "Sênior"
}
```
## Endpoints do usuário - SEM TOKEN

<h2 align ='center'> Cadastro (POST) </h2>

URL: http://localhost:3001/signup

```json
body: {
	"name": "Gabriela Marchiori",
	"email": "gabi@mail.com",
	"password": "12345",
	"linkedin": "/gabi",
	"level": "Junior",
	"bio": "Aprendendo a programar",
	"specialty": "Front-end",
	"isAdmin": false
}

Resposta: {
	"accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6ImdhYmlAbWFpbC5jb20iLCJpYXQiOjE2NjczMTI3NDQsImV4cCI6MTY2NzMxNjM0NCwic3ViIjoiMiJ9.HVFeefO-To1wQ013bBiwAroKBK1U57ZLMalodRdKUoI",
	"user": {
		"email": "gabi@mail.com",
		"name": "Gabriela Marchiori",
		"linkedin": "/gabi",
		"level": "Junior",
		"bio": "Aprendendo a programar",
		"specialty": "Front-end",
		"isAdmin": false,
		"id": 2
	}
}
```

<h2 align ='center'> Login (POST) </h2>

URL: http://localhost:3001/login

```json
body: {
	"email": "gabi@mail.com",
	"password": "12345"
}

Resposta: {
	"accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6ImdhYmlAbWFpbC5jb20iLCJpYXQiOjE2NjczMTU1OTAsImV4cCI6MTY2NzMxOTE5MCwic3ViIjoiMiJ9.FXeMkUvRpbF1vzsImNORtvMGIWpxdK38tN6M1JLdYwY",
	"user": {
		"email": "gabi@mail.com",
		"name": "Gabriela Marchiori",
		"linkedin": "/gabi",
		"level": "Pleno",
		"bio": "Aprendendo a programar",
		"specialty": "Front-end",
		"isAdmin": false,
		"id": 2
	}
}
```

<h2 align ='center'> Ver vagas disponíveis (GET) </h2>

URL: http://localhost:3001/companyJobs

## COM TOKEN

<h2 align ='center'> Ver informações do perfil (GET) </h2>

URL:  http://localhost:3001/users/2 
O 2 é o id do usuário

<h2 align ='center'> Editar perfil (PATCH) </h2>

URL:   http://localhost:3001/users/2
O 2 é o id do usuário

```json
body : {
	"level": "Pleno",
	"bio": "Aprendendo a programar",
	"specialty": "Front-end"
}
```

<h2 align ='center'> Salvar vagas (POST) </h2>

URL: http://localhost:3001/jobs

```json
body : {
  "userId": 2, (id do usuário)
  "company_name": "Teste Empresas 03",
  "specialty": "Back-end",
  "salary": "15000",
  "kind_of_work": "Remoto",
  "tech": [
    "React",
    "TypeScript",
    "Node.js"
  ],
  "level": "Júnior",
  "jobURL": "",
  "description": "Vaga destinada a júniors (2 a 4 anos de experiência), além disso é imprescíndivel que o programador tenha experiência com Node.js e TypeScript"
}
```

<h2 align ='center'> Ver vagas salvas (GET) </h2>

URL: http://localhost:3001/users/2?_embed=jobs
O 2 é referente ao id do usuário

```json
Resposta: {
	"email": "gabi@mail.com",
	"password": "$2a$10$EhtL.aRL2TF3OBXVqhl2fOnELSC1LB2tQ8OKADLL2nuTd0SB5Pw8.",
	"name": "Gabriela Marchiori",
	"linkedin": "/gabi",
	"level": "Pleno",
	"bio": "Aprendendo a programar",
	"specialty": "Front-end",
	"isAdmin": false,
	"id": 2,
	"jobs": [
		{
			"userId": 2,
			"company_name": "Teste Empresas 03",
			"specialty": "Back-end",
			"salary": "15000",
			"kind_of_work": "Remoto",
			"tech": [
				"React",
				"TypeScript",
				"Node.js"
			],
			"level": "Júnior",
			"jobURL": "",
			"description": "Vaga destinada a júniors (2 a 4 anos de experiência), além disso é imprescíndivel que o programador tenha experiência com Node.js e TypeScript",
			"id": 2
		}
	]
}
```

<h2 align ='center'> Deletar vaga salva (DELETE) </h2>

URL: http://localhost:3001/jobs/1 
O 1 é referente ao id da empresa que o usuário salvou como sua
Att.: O ID da empresa criada pelo admin é diferente do id que o usuário salva em seu perfil
