# Permitir Campanha com Múltiplos Códigos — Testes de API

Testes automatizados (Postman/Newman) dessa funcionalidade.

## Dashboard

[Ver dashboard de qualidade]([https://websupply.github.io/NOME-DO-REPOSITORIO/](https://adamcy11.github.io/CONNECT-MUTIPLASCAMPANHAS-QA/))

> Troque `NOME-DO-REPOSITORIO` pelo nome real do repositório assim que criar/transferir para a organização.

O dashboard mostra a taxa de sucesso, resultado por requisição, detalhamento de falhas e histórico das últimas execuções.

## Como funciona a pipeline

- Roda automaticamente toda segunda-feira às 08:00 (horário de Brasília).
- Também roda a cada `push`/`pull request` na branch principal.
- Pode ser disparada manualmente em Actions → **Run Postman API Tests - Multiplos Codigos** → Run workflow.
- Se algum teste falhar, um e-mail de alerta é enviado automaticamente para os destinatários configurados.
- O dashboard é publicado automaticamente no GitHub Pages a cada execução.

## Estrutura

```
.
├── .github/workflows/          # Workflow do GitHub Actions
├── scripts/
│   ├── generate-dashboard.js   # Gera o dashboard HTML
│   └── email-report.js         # Gera o e-mail de alerta
├── [QA] Permitir Campanha com Multiplos Codigos.postman_collection.json
└── package.json
```

## Rodando localmente

```
npm install
npx newman run "[QA] Permitir Campanha com Multiplos Codigos.postman_collection.json" --env-var "token=SEU_TOKEN"
```

## Secrets necessários (GitHub Actions)

| Secret | Descrição |
|---|---|
| `MAIL_USERNAME` | Conta Gmail usada para enviar os alertas |
| `MAIL_PASSWORD` | Senha de app do Gmail |
| `MAIL_TO` | E-mail(s) de destino dos alertas (separados por vírgula) |
| `MULTICODIGOS_TOKEN` | Token Bearer usado nos testes (autenticação da API) |
