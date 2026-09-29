# ✈️ Planejador de Viagem

Aplicação mobile full stack para **planejamento inteligente de viagens**, permitindo criar roteiros, descobrir destinos, organizar viagens com outras pessoas e receber sugestões personalizadas.

O projeto combina uma aplicação **React Native + Expo** com uma API em **NestJS**, persistência via **Prisma + SQLite** e integrações externas para IA, localização e clima.

---

## 📱 Sobre o projeto

O Planejador de Viagem foi desenvolvido para centralizar diferentes etapas da organização de uma viagem em uma única aplicação.

A partir do perfil e das preferências do usuário, a aplicação permite pesquisar destinos, receber sugestões de cidades, gerar roteiros, consultar detalhes do planejamento e compartilhar viagens por meio de organizações.

Além do planejamento individual, o sistema possui recursos sociais como **amizades** e **grupos de viagem**.

---

## ✨ Principais funcionalidades

- 🔐 Cadastro e autenticação de usuários
- 👤 Perfil e preferências pessoais
- 🌎 Pesquisa e escolha de destinos
- 🤖 Sugestões de cidades com apoio de IA
- 🗺️ Geração de roteiros de viagem
- 📍 Localização de atividades e pontos turísticos
- 🌦️ Informações de clima e temperatura
- 📅 Planejamento organizado por dias
- 💰 Definição de nível de gastos
- 🏨 Informações de hospedagem
- 👥 Sistema de amizades
- 🧳 Criação de organizações/grupos para viagens
- 📱 Interface mobile com navegação autenticada
- 💾 Persistência dos planejamentos e usuários

---

## 🧠 Inteligência Artificial

O backend possui integração com a **OpenAI API** para auxiliar na geração de sugestões relacionadas ao planejamento da viagem.

A arquitetura também prevê integrações com serviços externos para complementar as informações utilizadas pelo aplicativo, incluindo pesquisa de locais e dados meteorológicos.

---

## 🏗️ Arquitetura

O projeto está dividido em duas aplicações independentes:

```text
PlanejadorViagem/
│
├── backend/
│   ├── prisma/
│   └── src/
│       ├── core/
│       ├── modules/
│       │   ├── auth/
│       │   ├── friendship/
│       │   ├── openAi/
│       │   ├── organization/
│       │   ├── plan/
│       │   ├── preference/
│       │   └── user/
│       └── utils/
│
└── frontend/
    └── src/
        ├── routes/
        ├── screen/
        ├── services/
        ├── shared/
        ├── styles/
        └── types/
```

### Fluxo simplificado

```text
React Native / Expo
        │
        ▼
   REST API
        │
        ▼
      NestJS
   ┌────┼─────┐
   ▼    ▼     ▼
Prisma  IA   APIs externas
   │
   ▼
 SQLite
```

---

## 🛠️ Tecnologias

### Mobile

- React Native
- Expo
- TypeScript
- React Navigation
- TanStack Query
- Zustand
- React Hook Form
- Zod
- Axios
- Styled Components
- React Native Paper
- React Native Maps
- AsyncStorage

### Backend

- Node.js
- NestJS
- TypeScript
- Prisma ORM
- SQLite
- JWT
- Passport
- bcrypt
- OpenAI SDK
- Axios
- class-validator
- Jest

---

## 🗃️ Modelo de dados

Entre as principais entidades do sistema estão:

- **User** — usuários da aplicação
- **Preferences** — preferências pessoais
- **Plan** — planejamento principal da viagem
- **TripDay** — dias que compõem o roteiro
- **TouristActivity** — atividades e pontos turísticos
- **Friendship** — relações entre usuários
- **Organization** — grupos utilizados para viagens compartilhadas

Um planejamento armazena informações como destino, país, período da viagem, nível de gastos, hospedagem e localização geográfica.

Cada viagem pode possuir vários dias, e cada dia pode conter atividades turísticas, previsão do tempo, temperatura média e estimativa de gastos.

---

## 🔐 Autenticação

A aplicação utiliza autenticação baseada em **JWT**.

No mobile, o estado de autenticação controla automaticamente qual fluxo de navegação será apresentado:

```text
Não autenticado
      │
      ▼
Login / Cadastro

Autenticado
      │
      ▼
Home → Destinos → Roteiros → Perfil → Amigos → Organizações
```

---

## ⚙️ Configuração

### Pré-requisitos

Para executar o projeto localmente, tenha instalado:

- Node.js
- npm
- Expo
- Git

---

## 🚀 Executando o backend

Clone o repositório:

```bash
git clone https://github.com/willianminatto/PlanejadorViagem.git
cd PlanejadorViagem/backend
```

Instale as dependências:

```bash
npm install
```

Crie o arquivo `.env` a partir do exemplo disponível em `backend/.env.example`:

```env
DATABASE_URL=
jwtSecret=
openAiKey=
googleApi=
googleCx=
weatherApiKey=
```

Configure o banco com Prisma:

```bash
npx prisma generate
npx prisma migrate dev
```

Inicie a API:

```bash
npm run start:dev
```

---

## 📱 Executando o aplicativo

Em outro terminal:

```bash
cd PlanejadorViagem/frontend
npm install
```

Configure a URL da API no ambiente do frontend:

```env
BASE_URL="http://SEU_IP:3000/api"
```

> Em um dispositivo físico, utilize o IP da máquina que está executando o backend em vez de `localhost`.

Inicie o Expo:

```bash
npm start
```

Também é possível executar diretamente para uma plataforma:

```bash
npm run android
npm run ios
npm run web
```

---

## 🧪 Testes

O backend possui configuração com Jest.

```bash
cd backend

npm run test
npm run test:cov
npm run test:e2e
```

---

## 📌 Objetivo técnico

Este projeto explora a construção de uma aplicação full stack mobile envolvendo:

- arquitetura modular com NestJS;
- autenticação e autorização baseada em JWT;
- modelagem relacional com Prisma;
- consumo e integração de APIs externas;
- gerenciamento de estado no React Native;
- cache e sincronização de dados com TanStack Query;
- validação de formulários;
- recursos sociais entre usuários;
- integração de IA em uma aplicação real.

---

## 👨‍💻 Autores

Desenvolvido por:

- [Willian Minatto](https://github.com/willianminatto)
- [Luiz Felipe Zomer](https://github.com/LuizZomer)
- [Luiz Filipe Linhares](https://github.com/LuizFilipeLinhares)
