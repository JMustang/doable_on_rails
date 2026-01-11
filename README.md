# Doable On Rails

Um aplicativo de gerenciamento de tarefas (todos) e projetos desenvolvido com Ruby on Rails 8.1. Permite organizar tarefas dentro de projetos, com recursos de priorização e controle de status.

## 📋 Funcionalidades

### Projetos

- ✅ **CRUD completo** de projetos
- ✅ Criação, edição, visualização e exclusão de projetos
- ✅ Status de projeto (ativo/inativo)
- ✅ Visualização de todos associados a cada projeto
- ✅ Validação de nome obrigatório

### Todos (Tarefas)

- ✅ **CRUD completo** de todos
- ✅ Criação, edição, visualização e exclusão de tarefas
- ✅ Associação de todos a projetos
- ✅ Status de conclusão (completed/pending)
- ✅ Sistema de prioridade (1-5, sendo 5 a mais alta)
- ✅ Campo de descrição para detalhamento
- ✅ Visualização de todos por projeto ou globalmente

### Interface

- ✅ Interface moderna e responsiva com TailwindCSS
- ✅ Navegação intuitiva entre projetos e todos
- ✅ Mensagens de feedback (flash messages)
- ✅ Design consistente e acessível
- ✅ Suporte a JSON API (parcial)

## 🛠 Tecnologias

- **Ruby on Rails 8.1.1** - Framework web
- **SQLite3** - Banco de dados
- **TailwindCSS 4.4** - Estilização
- **Turbo Rails** - SPA-like navigation
- **Stimulus** - Framework JavaScript modesto
- **Puma** - Servidor web
- **Solid Cache/Queue/Cable** - Backend adapters para cache, jobs e websockets

## 🚀 Instalação e Configuração

### Pré-requisitos

- Ruby (versão compatível com Rails 8.1)
- Bundler
- Node.js (para assets)

### Passos

1. **Clone o repositório**

   ```bash
   git clone <url-do-repositorio>
   cd doable_on_rails
   ```

2. **Instale as dependências**

   ```bash
   bundle install
   ```

3. **Configure o banco de dados**

   ```bash
   bin/rails db:create
   bin/rails db:migrate
   bin/rails db:seed  # Opcional: dados iniciais
   ```

4. **Inicie o servidor**

   ```bash
   bin/dev
   ```

   Ou apenas:

   ```bash
   bin/rails server
   ```

5. **Acesse a aplicação**

```bash
   http://localhost:3000
   ```

## 🧪 Testes

O projeto utiliza o framework de testes padrão do Rails (Minitest).

### Executar testes

```bash
# Todos os testes
bin/rails test

# Testes de sistema
bin/rails test:system

# CI completo (inclui lint e segurança)
bin/ci
```

### Verificações de código

```bash
# Lint (RuboCop)
bin/rubocop

# Segurança (Brakeman)
bin/brakeman

# Auditoria de gems
bin/bundler-audit
```

## 📁 Estrutura do Projeto

```text
doable_on_rails/
├── app/
│   ├── controllers/     # ProjectsController, TodosController
│   ├── models/          # Project, Todo
│   ├── views/           # Views ERB com TailwindCSS
│   └── assets/          # Stylesheets e JavaScript
├── config/
│   ├── routes.rb        # Definição de rotas
│   └── database.yml     # Configuração do banco
├── db/
│   ├── migrate/         # Migrações do banco
│   └── schema.rb        # Esquema atual do banco
└── test/                # Testes
```

## 🗄 Modelo de Dados

### Project

- `id` - Identificador único
- `name` - Nome do projeto (obrigatório)
- `active` - Status ativo/inativo (boolean, default: true)
- `created_at`, `updated_at` - Timestamps
- **Relacionamento**: `has_many :todos`

### Todo

- `id` - Identificador único
- `name` - Nome da tarefa
- `description` - Descrição detalhada (text)
- `completed` - Status de conclusão (boolean, default: false)
- `priority` - Nível de prioridade (integer, default: 1, range: 1-5)
- `project_id` - Referência ao projeto (foreign key)
- `created_at`, `updated_at` - Timestamps
- **Relacionamento**: `belongs_to :project`

## 🔍 Melhorias Sugeridas

### Funcionalidades Prioritárias

1. **Autenticação e Autorização**
   - Sistema de usuários (Devise ou similar)
   - Controle de acesso (cada usuário vê apenas seus projetos/todos)
   - Sessões de usuário

2. **Validações e UX**
   - Validação de campos obrigatórios nos todos (nome)
   - Validação de prioridade (range 1-5)
   - Confirmação antes de deletar projetos com todos

3. **Filtros e Busca**
   - Busca de projetos e todos por nome
   - Filtro por status (completo/pendente)
   - Filtro por prioridade
   - Ordenação (por data, prioridade, nome)

4. **Datas e Prazos**
   - Data de criação visível
   - Data de vencimento para todos
   - Alertas de tarefas próximas ao vencimento
   - Filtro por data de vencimento

5. **Organização**
   - Tags ou categorias para todos
   - Arquivamento de projetos/todos (soft delete)
   - Drag and drop para reordenar

### Melhorias de Interface

1. **Dashboard**
   - Página inicial com estatísticas
   - Gráficos de progresso
   - Lista de todos urgentes
   - Resumo de projetos

2. **Experiência do Usuário**
   - Ações em lote (marcar múltiplos todos como completos)
   - Atalhos de teclado
   - Modo escuro
   - Notificações visuais

3. **PWA Completo**
   - Service Worker ativo
   - Instalação offline
   - Sincronização offline
   - Notificações push

### Melhorias Técnicas

1. **API e Integração**
   - API RESTful completa e documentada
   - Autenticação via token (JWT)
   - Rate limiting
   - Versionamento de API

2. **Performance**
    - Paginação de listas
    - Eager loading de associações
    - Cache de queries frequentes
    - Indexação adequada no banco

3. **Testes**
    - Aumentar cobertura de testes
    - Testes de integração mais completos
    - Testes de performance
    - Testes E2E

4. **Deploy e DevOps**
    - Configuração de produção
    - CI/CD pipeline completo
    - Monitoramento e logging
    - Backup automático do banco

## 📝 Próximos Passos

### Curto Prazo (1-2 semanas)

- ✅ Adicionar autenticação básica de usuários
- ✅ Implementar validações mais robustas
- ✅ Adicionar busca simples por nome
- ✅ Configurar root route (redirecionar para projetos ou dashboard)
- ✅ Melhorar mensagens de erro e feedback

### Médio Prazo (1 mês)

- ✅ Implementar filtros (status, prioridade)
- ✅ Adicionar data de vencimento aos todos
- ✅ Criar dashboard com estatísticas
- ✅ Melhorar testes (aumentar cobertura)
- ✅ Adicionar paginação

### Longo Prazo (2-3 meses)

- ✅ Implementar tags/categorias
- ✅ Adicionar modo offline (PWA completo)
- ✅ Criar API pública documentada
- ✅ Implementar notificações
- ✅ Preparar para deploy em produção

---
