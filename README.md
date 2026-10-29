# Radar Saúde — Painel Admin

Painel web de administração do Radar Saúde (Angular 21, Reactive Forms, Leaflet): login de
administrador, cadastro e edição de hospitais, ativação e desativação, bloqueio de escrita
de feedback, moderação de sugestões e dashboard de indicadores.

## Repositórios do projeto

| Repositório | Conteúdo |
|---|---|
| [radar-saude-mobile](https://github.com/devpointinnovations/radar-saude-mobile) | App Expo / React Native |
| **painel-admin-frontend** (este) | Painel Admin Angular |
| [radar-saude-backend](https://github.com/devpointinnovations/radar-saude-backend) | API Spring Boot, deploy no Cloud Run, testes de desempenho |
| [radar-saude-docs](https://github.com/devpointinnovations/radar-saude-docs) | Documentação, ADRs, backlog, registros de homologação e site |

Até 29/10/2026 o painel era a pasta `admin/` do monorepo
[GabrielVogado/saude-monitor](https://github.com/GabrielVogado/saude-monitor). O histórico
desta pasta foi preservado aqui; PRs antigos citados nas mensagens de commit (`#123`) são
daquele repositório.

## Rodando localmente

Requer Node 20.19+ e npm 11.6.1 (o lockfile foi gerado com ele).

```bash
npm install -g npm@11.6.1
npm ci
npm start          # ng serve em http://localhost:4200
npm test           # Vitest
npm run build      # build de produção em dist/
```

A URL da API fica em `src/app/app.config.ts` (`API_BASE_URL`), hoje apontando para o
backend de desenvolvimento no Cloud Run.

## CI

O `.github/workflows/ci.yml` roda em push para `develop` e `master` e em PR: testes com
cobertura, mínimo de 90% nas linhas alteradas (diff-cover), trava de contagem de testes,
análise no SonarQube Cloud (com o segredo `SONAR_TOKEN`) e build. A `master` só aceita PR
vindo da `develop` (`pr-origem-master.yml`). Os rulesets de proteção ficam em
`.github/rulesets/`.

Git-flow, convenções e regras do projeto: `Documentos/10-git-flow/MANUAL.md` no
[radar-saude-docs](https://github.com/devpointinnovations/radar-saude-docs).
