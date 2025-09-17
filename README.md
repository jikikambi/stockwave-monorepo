# StockWave Monorepo

StockWave is a full-stack monorepo starter setup designed for multiple frontend frameworks and microservices. It uses Nx for orchestration and currently includes React, Vue, Angular, and .NET microservices. This repository represents the **initial setup** and will serve as the foundation for future development.

> ⚠️ **Note:** This is a startup scaffold. The project structure, apps, and libraries are set up, but no business logic or features have been implemented yet.

## Repository Structure

```

stockwave/
├── backend-dotnet/             # .NET Minimal API microservices
├── backend-fastify/            # Fastify microservices
├── frontend/
│     ├── react-app/            # React frontend (Redux + Tailwind + Vite + Vitest)
│     ├── vue-app/              # Vue frontend (Pinia + vue-query + Vite + Vitest)
│     ├── angular-app/          # Angular frontend (NgRx Data/Entity)
├── libs/                       # Shared code (models, API clients, UI components)
│     ├── api-client/           # Shared API client code
│     ├── ui/                   # Shared UI components
├── docker-compose.dev.yml      # Dev infra (SQL, Mongo, Redis, RabbitMQ, backend)
├── docker-compose.ci.yml       # CI infra
├── Makefile                    # Start/stop infra & apps
├── dev-helpers.sh              # Healthchecks
├── nx.json / package.json      # Monorepo tooling
└── README.md                   # Project documentation

```

## Getting Started

### Prerequisites

- Node.js >= 20  
- npm >= 10  
- .NET SDK >= 8 (for backend-dotnet)  
- Docker & Docker Compose (for local infra)

### Setup

```bash
# Clone the repo
git clone https://github.com/jikikambi/stockwave-monorepo.git
cd stockwave-monorepo

# Install dependencies
npm install

# Reset Nx cache
npx nx reset
````

### Running Frontend Apps

```bash
# Serve React app
npx nx serve react-app

# Serve Vue app
npx nx serve vue-app

# Serve Angular app
npx nx serve angular-app
```

### Running Tests

```bash
# Run unit tests for a specific project
npx nx test <project-name>

# Run E2E tests (Cypress/Playwright)
npx nx e2e <project-name>-e2e
```

### Nx Tools

* Visualize project dependencies:

```bash
npx nx graph
```

* List all available targets for a project:

```bash
npx nx show project <project-name> --web
```

### Tailwind Setup

* React app: configured with Nx + Tailwind + Vite
* Vue app: configured with Nx + Tailwind + Vite
* Angular app: configured with Nx + Tailwind (SCSS optional)

### Docker Development Environment

```bash
# Start development services
docker-compose -f docker-compose.dev.yml up
```

## Future Work

This monorepo is intended to evolve with:

* Implementation of microservices in `backend-dotnet` and `backend-fastify`
* Adding more frontend features in React, Vue, and Angular apps
* Enhancing shared libraries (`libs/api-client`, `libs/ui`)
* CI/CD pipelines using Docker Compose and Nx caching

## Contributing

* Add features in apps or shared libs under `libs/`
* Follow Nx best practices for project structure
* Unit tests for new logic are required

## MIT License

```
Copyright (c) 2025

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.

```
