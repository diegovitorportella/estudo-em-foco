# 📚 Estudo em Foco

> Pomodoro com histórico: cronometre sessões de estudo por matéria, acompanhe metas semanais, sequência de dias (streak) e um mapa de calor da sua consistência.

![Status](https://img.shields.io/badge/status-planejamento-blue)
![Angular](https://img.shields.io/badge/Angular-21-dd0031)
![NestJS](https://img.shields.io/badge/NestJS-API-e0234e)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-dados-336791)
![RxJS](https://img.shields.io/badge/RxJS-7-b7178c)
![License](https://img.shields.io/badge/license-MIT-green)

---

## 📑 Sumário

1. [Nome e Descrição](#1-nome-e-descrição)
2. [Objetivo e Problema Resolvido](#2-objetivo-e-problema-resolvido)
3. [Público-alvo](#3-público-alvo)
4. [Funcionalidades do MVP](#4-funcionalidades-do-mvp)
5. [Funcionalidades Futuras](#5-funcionalidades-futuras)
6. [Stack Tecnológica e Justificativas](#6-stack-tecnológica-e-justificativas)
7. [Arquitetura e Organização](#7-arquitetura-e-organização)
8. [Estrutura Inicial de Pastas](#8-estrutura-inicial-de-pastas)
9. [Plano de Desenvolvimento Passo a Passo](#9-plano-de-desenvolvimento-passo-a-passo)
10. [Boas Práticas e Padrões de Código](#10-boas-práticas-e-padrões-de-código)
11. [Desafios Técnicos e Conhecimentos Desenvolvidos](#11-desafios-técnicos-e-conhecimentos-desenvolvidos)
12. [Evolução Futura](#12-evolução-futura)

---

## 1. Nome e Descrição

**Estudo em Foco** é uma aplicação web para quem estuda com a técnica Pomodoro e quer **medir a própria constância**. O usuário cadastra matérias, inicia ciclos de foco e pausa, e o sistema registra cada sessão e transforma o histórico em metas, sequência de dias e relatórios.

O projeto é **cliente-servidor clássico**, pensado como projeto de entrada:

- **Front-end (Angular):** timer Pomodoro, telas de matérias, histórico, estatísticas e um **componente de mapa de calor** próprio.
- **Back-end (NestJS + PostgreSQL):** autentica o usuário, guarda as sessões e calcula agregados por dia e semana, além do streak.

> **Diferença de um CRUD genérico:** o valor está no **timer confiável** (RxJS), no **cálculo de streak com fuso horário** e no **mapa de calor** construído por você, sem biblioteca pronta.

## 2. Objetivo e Problema Resolvido

### Problema
Estudar sem medir é difícil de manter: a pessoa não sabe quanto estudou na semana, em qual matéria foca menos e se está sendo consistente. Timers comuns não guardam histórico.

### Objetivo
- **Iniciar uma sessão em um toque** e deixar o timer cuidar do resto.
- **Registrar automaticamente** cada sessão concluída, ligada a uma matéria.
- **Motivar a constância** com meta semanal, streak e mapa de calor.
- **Revisar a semana** com um relatório simples.

### Objetivo de aprendizado
Praticar **RxJS de verdade** (timer, cancelamento, combinação de streams), **Signals**, componentes visuais customizados e formulários no front-end; no back-end, **API autenticada, modelagem relacional, agregações por data e fuso horário**.

## 3. Público-alvo

- **Estudantes** de escola, faculdade e cursos.
- **Concurseiros** e quem se prepara para provas longas.
- **Desenvolvedores em transição de carreira** que estudam em paralelo ao trabalho.
- **Recrutadores e desenvolvedores**, como vitrine de RxJS, UI customizada e API bem estruturada.

## 4. Funcionalidades do MVP

### Front-end
| # | Funcionalidade | Descrição |
|---|---|---|
| 1 | **Cadastro e login** | Criar conta, entrar, sair e renovar a sessão automaticamente. |
| 2 | **Matérias** | CRUD com nome, cor e meta semanal (em minutos). |
| 3 | **Timer Pomodoro** | Ciclos de foco, pausa curta e pausa longa; iniciar, pausar, retomar e abandonar. |
| 4 | **Configuração do Pomodoro** | Duração do foco, das pausas e quantos ciclos até a pausa longa. |
| 5 | **Registro automático** | Ao concluir um foco, a sessão é salva ligada à matéria escolhida. |
| 6 | **Recuperação do timer** | Recarregar ou fechar a aba não perde o ciclo em andamento. |
| 7 | **Alerta de fim** | Som e notificação do navegador quando o ciclo termina. |
| 8 | **Histórico de sessões** | Lista paginada com filtro por matéria e período; adicionar sessão manual. |
| 9 | **Meta semanal** | Barra de progresso por matéria (estudado × meta). |
| 10 | **Streak** | Dias seguidos com estudo, mais o recorde pessoal. |
| 11 | **Mapa de calor** | Grade de dias estilo GitHub, com intensidade por minutos estudados. |
| 12 | **Relatório semanal** | Total da semana, comparação com a anterior, distribuição por matéria. |
| 13 | **Responsivo e tema** | Funciona bem no celular; tema claro e escuro. |

### Back-end
| # | Funcionalidade | Descrição |
|---|---|---|
| 14 | **Autenticação** | Cadastro, login, access token de vida curta e refresh token. |
| 15 | **API de matérias** | CRUD isolado por usuário. |
| 16 | **API de sessões** | Criar, listar com filtros e paginação, editar e excluir. |
| 17 | **Configurações do usuário** | Preferências do Pomodoro e **fuso horário**. |
| 18 | **Estatísticas** | Resumo do dia, semana, mapa de calor, streak e relatório semanal. |
| 19 | **Documentação da API** | Especificação OpenAPI navegável (Swagger). |

**Fora do MVP:** estudo em grupo, ranking entre amigos, sincronização entre dispositivos do timer em tempo real, aplicativo móvel nativo.

## 5. Funcionalidades Futuras

- **Estudar em grupo** com salas e ranking semanal.
- **Planejamento de revisão** (repetição espaçada).
- **Tarefas** vinculadas às matérias (o que estudar em cada sessão).
- **Ruído branco/música de foco** integrados.
- **Metas diárias** e conquistas (badges).
- **Exportar relatórios** em PDF/CSV.
- **PWA** instalável e timer em segundo plano.
- Internacionalização (pt-BR, en).
- Anotações rápidas por sessão.

## 6. Stack Tecnológica e Justificativas

| Camada | Tecnologia | Justificativa |
|---|---|---|
| Front | **Angular (estável atual) + TypeScript strict** | Formulários robustos e estrutura opinativa. |
| Front | **RxJS** | `timer`/`interval`, `takeUntil`, `combineLatest`, `switchMap`: o coração do timer. |
| Front | **Signals** | Estado do timer e da UI de forma simples e reativa. |
| Front | **Reactive Forms (tipados)** | Matérias e configurações do Pomodoro. |
| Front | **Web APIs (Notifications, Audio, `localStorage`, Page Visibility)** | Alertas e recuperação do ciclo em andamento. |
| Front | **Componente de heatmap próprio (CSS Grid/SVG)** | Aprender a construir UI sem depender de biblioteca. |
| Front | **Chart.js (via ng2-charts) ou ECharts** | Gráfico do relatório semanal. |
| Front | **SCSS + CSS variables** | Tema claro/escuro e responsividade. |
| Back | **NestJS (TypeScript)** | Estrutura modular parecida com Angular; validação, guards e Swagger integrados. |
| Back | **PostgreSQL + TypeORM com migrations** | Timestamps, agregações por intervalo e schema versionado. |
| Back | **class-validator / class-transformer** | Validação dos DTOs. |
| Back | **JWT (access + refresh) + bcrypt/argon2** | Padrão para API stateless; senha com hash forte. |
| Back | **Luxon ou date-fns-tz** | Cálculos de dia e semana respeitando o fuso do usuário. |
| Infra | **Docker Compose** | Banco e API reproduzíveis com um comando. |
| Qualidade | **Jest (front e back) + Supertest** | Regras de streak, timer, API e isolamento testados. |
| Qualidade | **ESLint + Prettier + CI** | Consistência e feedback automático. |

> **Decisão — o timer calcula pelo relógio, não por "ticks":** navegadores reduzem a frequência de timers em abas inativas. Por isso o tempo restante é sempre `fim previsto − agora`, e o `interval` serve **apenas para atualizar a tela**. É assim que o ciclo continua correto após minimizar a aba ou recarregar a página.

> **Decisão — datas em UTC, "dia" no fuso do usuário:** sessões são guardadas em UTC (`timestamptz`). O que conta como "dia" para streak e mapa de calor é calculado no **fuso configurado pelo usuário**, evitando que estudar às 23h30 caia no dia seguinte.

> **Decisão — sem monorepo com pacotes compartilhados:** `frontend/` e `backend/` são independentes, como projeto de entrada.

## 7. Arquitetura e Organização

### 7.1 Visão geral

```
┌────────────── FRONT-END (Angular) ──────────────┐
│ Páginas → Serviços (Signals/RxJS)                │
│              │                                   │
│        TimerService (RxJS)  ←→  localStorage     │
│              │ (ao concluir um foco)             │
│        HttpClient + Interceptors                 │
└────────────────────────┬────────────────────────┘
                         │ HTTPS / JSON
                         ▼
┌────────────── BACK-END (NestJS) ────────────────┐
│ Controllers → Services → Repositories (TypeORM)  │
│   │ Guards (JWT)  │ DTOs/Pipes de validação      │
│                   ▼                              │
│              PostgreSQL                          │
└──────────────────────────────────────────────────┘
```

### 7.2 Como o timer funciona
1. Ao iniciar, o app grava no `localStorage` o estado do ciclo: tipo (foco/pausa), matéria, `startedAt`, duração prevista e se está pausado (com o tempo acumulado de pausa).
2. Um `interval(250ms)` apenas **dispara a releitura** do tempo restante: `restante = duração − (agora − startedAt − pausado)`.
3. Quando `restante <= 0`, o `TimerService` emite "ciclo concluído": toca o som, mostra a notificação e, se era um **foco**, envia `POST /sessions`.
4. Se a rede falhar, a sessão fica numa fila local simples e é reenviada na próxima oportunidade (sem perder o estudo).
5. Ao abrir o app, o serviço lê o `localStorage`: se há um ciclo em andamento, **retoma** de onde está; se já expirou enquanto o app estava fechado, oferece "registrar sessão" ou descartar.

> O estado do timer vive **no front-end**; o servidor só recebe **sessões concluídas**. Isso mantém o MVP simples e sem WebSocket.

### 7.3 Como o streak é calculado
- Um **dia conta** se houver ao menos **uma sessão de foco concluída** (regra configurável no futuro: mínimo de minutos).
- O dia é determinado pelo fuso do usuário.
- **Streak atual:** dias consecutivos terminando **hoje** — ou **ontem**, se hoje ainda não teve sessão (o streak só quebra quando o dia termina sem estudo).
- **Recorde:** maior sequência já registrada.
- O cálculo é uma **função pura** (`calculateStreak(datas, hoje)`), 100% testável, usada pelo service do back-end.

### 7.4 Comunicação Front ↔ Back
- API **REST em JSON**, prefixo `/api/v1`.
- Autenticação por header `Authorization: Bearer <accessToken>`.
- **Interceptor de autenticação** adiciona o token; ao receber `401`, tenta **uma** renovação com o refresh token e repete a requisição. Se falhar, desloga.
- **Interceptor de erros** converte o erro padrão da API em mensagem ao usuário.
- Instantes trafegam em **ISO 8601 UTC**; datas de calendário (`YYYY-MM-DD`) já vêm calculadas no fuso do usuário nos endpoints de estatística.
- **Erro padronizado:** `{ "statusCode": 400, "error": "Bad Request", "message": ["..."] }`.
- **CORS** liberado apenas para a origem do front-end.

### 7.5 Princípios
- **Funções puras para regras** (streak, intervalo da semana, progresso de meta), fora de componentes e services.
- **Isolamento por usuário:** toda consulta filtra pelo `userId` do token; testado explicitamente.
- **Agregação no banco:** soma por dia e por matéria com `SUM` + `GROUP BY`.
- **Timer desacoplado da UI:** o `TimerService` não conhece componentes; a tela só observa um estado.
- **Sem `subscribe` solto:** usar `async` pipe, `toSignal` e `takeUntilDestroyed`.

### 7.6 Autenticação e autorização
1. **Cadastro:** valida e-mail único, aplica hash na senha e cria as configurações padrão (Pomodoro 25/5/15, fuso detectado pelo navegador).
2. **Login:** devolve `accessToken` (≈15 min) e `refreshToken` (≈7 dias).
3. **Refresh token:** guardado **com hash** no banco, **rotacionado** a cada uso e revogado no logout.
4. **Autorização:** `JwtAuthGuard` global, exceto rotas públicas. Não há papéis: cada usuário acessa apenas o que é seu.
5. Recurso de outro usuário responde **404**.

### 7.7 Modelo de dados (inicial)

```
users                       subjects
─────                       ────────
id (uuid, PK)               id (uuid, PK)
name                        user_id (FK → users)
email (unique)              name
password_hash               color
created_at                  weekly_goal_minutes (int, nullable)
                            archived_at (nullable)
                            UNIQUE (user_id, name)

user_settings               study_sessions
─────────────               ──────────────
user_id (PK, FK → users)    id (uuid, PK)
focus_minutes (int)         user_id (FK → users)
short_break_minutes (int)   subject_id (FK → subjects)
long_break_minutes (int)    started_at (timestamptz)
cycles_until_long (int)     ended_at (timestamptz)
timezone (text)             duration_seconds (int, > 0)
                            source ('timer' | 'manual')
refresh_tokens              note (text, nullable)
──────────────              created_at
id, user_id, token_hash,
expires_at, revoked_at      Índices:
                             (user_id, started_at)
                             (user_id, subject_id, started_at)
```

**Regras de integridade:**
- Só **sessões de foco concluídas** são persistidas (pausas não vão para o banco).
- `duration_seconds > 0` e `ended_at > started_at`.
- Matéria com sessões não é excluída: é **arquivada** (`archived_at`), preservando o histórico.
- A sessão pertence à matéria **do mesmo usuário** (validar no service).
- Para evitar duplicidade em reenvios, a sessão carrega um **`id` gerado no cliente** (UUID); `POST /sessions` com o mesmo `id` não cria outra.

### 7.8 Contratos principais da API

Todas as rotas abaixo (exceto `auth/*` e `health`) exigem `Authorization: Bearer`.

| Recurso | Método e rota | Descrição |
|---|---|---|
| Auth | `POST /auth/register` | Cria conta. Body: `name`, `email`, `password`. |
| Auth | `POST /auth/login` | Retorna `accessToken` e `refreshToken`. |
| Auth | `POST /auth/refresh` | Troca o refresh token por um novo par. |
| Auth | `POST /auth/logout` | Revoga o refresh token. |
| Usuário | `GET /me` | Dados do usuário. |
| Configurações | `GET /settings` · `PUT /settings` | Preferências do Pomodoro e fuso horário. |
| Matérias | `GET /subjects` (`?includeArchived=`) | Lista. |
| Matérias | `POST /subjects` · `PATCH /subjects/:id` | Cria e edita (inclui arquivar). |
| Sessões | `GET /sessions` | Lista com filtros (`subjectId`, `from`, `to`) e paginação. |
| Sessões | `POST /sessions` | Registra sessão (do timer ou manual). Idempotente pelo `id`. |
| Sessões | `PATCH /sessions/:id` · `DELETE /sessions/:id` | Edita e exclui. |
| Estatísticas | `GET /stats/today` | Minutos e sessões de hoje. |
| Estatísticas | `GET /stats/heatmap?from=&to=` | Minutos por dia. |
| Estatísticas | `GET /stats/streak` | Streak atual e recorde. |
| Estatísticas | `GET /stats/weekly?weekStart=2026-11-02` | Relatório da semana. |
| Estatísticas | `GET /stats/goals?weekStart=2026-11-02` | Progresso das metas semanais por matéria. |
| Saúde | `GET /health` | Verificação de status. |

**Exemplo — registrar sessão**

```json
POST /api/v1/sessions
{
  "id": "0b7c0f0e-5f0e-4d1e-9a52-3b7e0a6a1c11",
  "subjectId": "…",
  "startedAt": "2026-11-06T18:00:00Z",
  "endedAt": "2026-11-06T18:25:00Z",
  "durationSeconds": 1500,
  "source": "timer"
}
```

**Exemplo — mapa de calor**

```json
GET /api/v1/stats/heatmap?from=2026-08-10&to=2026-11-06
{
  "timezone": "America/Sao_Paulo",
  "days": [
    { "date": "2026-11-05", "minutes": 75, "sessions": 3 },
    { "date": "2026-11-06", "minutes": 25, "sessions": 1 }
  ]
}
```

(Dias sem estudo podem ser omitidos; o front completa com zero.)

**Exemplo — relatório semanal**

```json
GET /api/v1/stats/weekly?weekStart=2026-11-02
{
  "weekStart": "2026-11-02",
  "totalMinutes": 540,
  "previousWeekMinutes": 420,
  "bySubject": [
    { "subjectId": "…", "name": "Matemática", "minutes": 300 },
    { "subjectId": "…", "name": "Inglês", "minutes": 240 }
  ],
  "byDay": [
    { "date": "2026-11-02", "minutes": 90 }
  ]
}
```

## 8. Estrutura Inicial de Pastas

```
estudo-em-foco/
├── README.md
├── docker-compose                # PostgreSQL + API
├── .github/                      # CI: lint, testes, build
├── backend/
│   ├── .env.example
│   ├── migrations/
│   └── src/
│       ├── main
│       ├── config/               # variáveis de ambiente validadas
│       ├── common/               # guards, filtros de erro, decorators, paginação
│       └── modules/
│           ├── auth/
│           ├── users/
│           ├── settings/
│           ├── subjects/
│           ├── sessions/
│           └── stats/            # agregações, streak (função pura), semana
└── frontend/
    └── src/
        ├── assets/sounds/        # alerta de fim de ciclo
        ├── styles/               # tokens, tema claro/escuro
        └── app/
            ├── core/
            │   ├── auth/         # serviço, guard, interceptors
            │   ├── http/
            │   └── services/     # tema, notificações do navegador, fila de reenvio
            ├── shared/           # UI, pipes (duração, data), componente de heatmap
            └── features/
                ├── auth/
                ├── timer/        # TimerService, tela do Pomodoro, seletor de matéria
                ├── subjects/
                ├── history/
                ├── stats/        # streak, heatmap, relatório semanal
                └── settings/
```

## 9. Plano de Desenvolvimento Passo a Passo

Estimativa em ritmo parcial: **7 a 9 semanas**. Dica: **o timer funciona sem back-end** nas primeiras fases; a API entra quando o núcleo já está pronto.

### Fase 0 — Fundação (3 a 4 dias)
- [ ] Criar `frontend/` (Angular) e `backend/` (NestJS) com TypeScript strict.
- [ ] Configurar ESLint, Prettier, Jest e CI.
- [ ] Subir PostgreSQL com Docker Compose e variáveis de ambiente validadas.
- [ ] Definir tokens de design e tema claro/escuro.

### Fase 1 — Timer no front-end (1,5 a 2 semanas) — **núcleo do app**
- [ ] `TimerService` com estado (foco, pausa curta, pausa longa; rodando, pausado, parado).
- [ ] Tempo restante calculado pelo relógio (`fim − agora`), com `interval` só para a tela.
- [ ] Iniciar, pausar, retomar e abandonar.
- [ ] Persistência do ciclo em `localStorage` e recuperação ao reabrir.
- [ ] Alerta sonoro, notificação do navegador e título da aba com o tempo.
- [ ] Testes do serviço com `fakeAsync` e relógio controlado (pausa, retomada, aba em segundo plano, ciclo expirado enquanto fechado).

### Fase 2 — Back-end e autenticação (1,5 semana)
- [ ] Aplicação NestJS, configuração validada e rota de saúde.
- [ ] Entidade `User`, cadastro, login, hash, access e refresh token, guard global e rate limiting.
- [ ] Front: telas de login/cadastro, guard de rota e interceptor de renovação.
- [ ] Testes: e-mail duplicado, senha errada, token expirado, refresh rotacionado.

### Fase 3 — Matérias e sessões (2 semanas)
- [ ] Back: CRUD de matérias (com arquivamento) e de sessões (filtros, paginação, idempotência pelo `id`).
- [ ] Front: tela de matérias e seletor no timer.
- [ ] Front: envio da sessão ao concluir o foco, com **fila de reenvio** se estiver offline.
- [ ] Front: histórico com filtros e sessão manual.
- [ ] Testes: isolamento por usuário, reenvio duplicado, matéria de outro usuário.

### Fase 4 — Configurações e fuso horário (3 a 4 dias)
- [ ] Back: `GET/PUT /settings` com validação de limites (ex.: foco entre 5 e 120 min).
- [ ] Front: tela de configurações; o timer passa a usar as preferências.
- [ ] Detectar o fuso do navegador no cadastro.

### Fase 5 — Estatísticas (2 semanas)
- [ ] Função pura `calculateStreak` com testes de borda (virada de dia, fuso, hoje sem estudo, recorde).
- [ ] Endpoints `today`, `streak`, `heatmap`, `weekly` e `goals` com agregações SQL no fuso do usuário.
- [ ] Front: **componente de heatmap** (grade por semanas, escala de intensidade, tooltip, acessível por teclado).
- [ ] Front: barras de meta semanal e gráfico do relatório.
- [ ] Testes: sessão às 23h30 e à 00h30 em fusos diferentes, mudança de semana, semana sem dados.

### Fase 6 — Acabamento e entrega (1 semana)
- [ ] Revisar acessibilidade (timer anunciado a leitores de tela, foco, contraste).
- [ ] Revisar responsividade e performance.
- [ ] Documentação Swagger revisada.
- [ ] Empacotar com Docker e publicar front e API em hospedagem gratuita.
- [ ] README final com capturas de tela, GIF do timer e do heatmap.

## 10. Boas Práticas e Padrões de Código

**Geral**
- TypeScript strict, sem `any`.
- Commits pequenos (*Conventional Commits*); nomes no código em inglês.
- **Nunca** commitar segredos; usar `.env.example`.
- Uma branch por funcionalidade e *pull request* para si mesmo, descrevendo o que mudou e como testou.

**Front-end**
- Componentes *standalone*, `OnPush` e *lazy loading* por feature.
- `TimerService` sem dependência de componentes; estado exposto via Signals/Observables.
- Cancelar streams corretamente (`takeUntilDestroyed`, `switchMap`) para não vazar `interval`.
- Nunca confiar em contagem de "ticks": sempre o relógio.
- Tratar permissões negadas (notificação, áudio bloqueado) com *fallback* visual.
- Acessibilidade: `aria-live` moderado no timer (não anunciar todo segundo), foco visível, contraste, heatmap com alternativa em texto.

**Back-end**
- Validar toda entrada com DTOs; whitelist de propriedades.
- Respostas de erro padronizadas; não vazar detalhes internos.
- Migrations versionadas; nada de `synchronize: true`.
- **Toda consulta filtrada pelo usuário autenticado.**
- Regras de data em funções puras; instantes em UTC, dia calculado no fuso do usuário.
- Hash forte de senha; não registrar dados sensíveis em log.

**Testes e validação**
- **Unitários:** `calculateStreak`, intervalo da semana, progresso de meta, `TimerService`.
- **Integração/API (Supertest + banco de teste):** autenticação, sessões idempotentes, estatísticas por fuso e isolamento entre usuários.
- **Front:** testes de serviços, do formulário de configurações e do componente de heatmap (entrada → células/intensidades).
- **Critério de pronto de cada fatia:** funciona na tela, tem teste da regra principal, está documentado no Swagger e passa no CI.

## 11. Desafios Técnicos e Conhecimentos Desenvolvidos

| Desafio | O que você aprende |
|---|---|
| Timer que não "deriva" | RxJS, cálculo por relógio, Page Visibility, `fakeAsync` |
| Recuperar o ciclo após recarregar | `localStorage`, serialização de estado, casos de borda |
| Streams bem comportados | `interval`, `takeUntil`, `switchMap`, `combineLatest`, ausência de vazamentos |
| Componente de heatmap próprio | CSS Grid/SVG, escala de cores, acessibilidade, testes de componente |
| Datas e fuso horário | UTC × dia local, `AT TIME ZONE`, virada de dia e de semana |
| Cálculo de streak | Funções puras, TDD, casos de borda |
| Idempotência no envio | ID gerado no cliente, fila de reenvio, reenvio seguro |
| Agregações por dia e semana | `SUM`, `GROUP BY`, `date_trunc`, índices |
| Autenticação com refresh de token | JWT, rotação, guards, interceptors |
| Isolamento entre usuários | Autorização por propriedade, testes de segurança |
| Docker e CI | Ambiente reproduzível e pipeline automatizado |

## 12. Evolução Futura

- **Tarefas por matéria** e plano de estudo semanal.
- **Revisão espaçada** (lembrar de revisar o conteúdo após N dias).
- **Estudo em grupo** com salas e ranking (WebSocket/SSE).
- **PWA** com timer e notificações em segundo plano (Service Worker).
- **Conquistas** e metas diárias configuráveis.
- **Exportação** de relatórios em PDF/CSV.
- **Testes ponta a ponta** (Playwright): iniciar foco → concluir → ver no histórico e no heatmap.
- **Recuperação de senha** por e-mail e login social.
- **Cache** de estatísticas, se a carga justificar.

---

## 📝 Notas Finais

- Este documento é um **guia de planejamento**; ajuste o escopo ao seu ritmo.
- Construa **o timer primeiro, sem back-end**: é a parte mais divertida e a que mais ensina RxJS.
- Ao fim de cada fase, atualize os checkboxes e registre o que aprendeu.
