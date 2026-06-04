# CodeConnect (Versão Divulgação de Desenvolvedores)

<img width="1896" height="907" alt="Image" src="https://github.com/user-attachments/assets/41046e43-372d-4b27-9b1e-1243e31d6b6a" />


O projeto CodeConnect consistiu no desenvolvimento de uma plataforma web responsiva de networking para atender a necessidade dos desenvolvedores, combinando segurança avançada e recursos de conexão em um ambiente otimizado para desktop e dispositivos móveis. Em termos de segurança, o sistema conta com cadastro e login validados em tempo real, medidor de força de senha, autenticação social via Google OAuth, rotas protegidas e renovação automatizada de sessão via *Refresh Tokens* baseados em JWT. Para a interação dos usuários, a plataforma disponibiliza o gerenciamento de perfil com seleção de especialidades técnicas, um feed dinâmico com a listagem dos profissionais cadastrados e um canal integrado de envio de mensagens para contato direto entre os membros.

## Funcionalidades Principais

### Autenticação e Segurança
* **Login Tradicional e Social**: Suporte a login convencional por e-mail e senha, além de integração nativa para autenticação social via Google (redirecionando para fluxos OAuth).
* **Validação Estrita com Zod**: Formulários protegidos com esquemas de validação em tempo real para login e cadastro de novos usuários.
* **Medidor de Força de Senha**: O formulário de cadastro analisa dinamicamente a complexidade da senha digitada (comprimento, letras maiúsculas/minúsculas, números e caracteres especiais), exibindo um indicador visual que varia de "Muito Fraca" a "Muito Forte".
* **Gerenciamento de Sessão Constante**: Armazenamento seguro de estado com `Context API`. Os dados do usuário são persistidos localmente (`localStorage`), garantindo que a sessão não seja perdida ao atualizar a página.
* **Renovação Automática de Token (Silent Refresh)**: Monitoramento ativo do tempo de expiração do JWT (através de `jwt-decode`). O sistema renova o token automaticamente 60 segundos antes de sua expiração em segundo plano, evitando deslogamentos abruptos.
* **Rotas Protegidas**: Controle de acesso global onde usuários não autenticados são interceptados e redirecionados para a tela de login.

### Perfil do Desenvolvedor e Categorização
* **Customização do Perfil**: Permite que o usuário atualize seu nome, e-mail, biografia/descrição e redefina sua senha.
* **Seleção de Especialidades**: Menu interativo de caixas de seleção para vincular o perfil a categorias específicas do mercado de tecnologia, como: `FullStack`, `Front`, `Mobile`, `Back`, `DevOps` e `Data`.

### Conexão e Feed
* **Feed de Desenvolvedores**: Consumo centralizado e listagem de profissionais cadastrados na plataforma através de um contexto global dedicado.
* **Formulário de Contato Direto**: Canal de comunicação interna validado onde visitantes podem preencher nome, e-mail e redigir mensagens direcionadas a um desenvolvedor específico.

### Interface Responsiva (UI/UX)
* **Navegação Adaptável**: Menu lateral de navegação expandido (`DesktopNav`) projetado para telas maiores, e uma barra de navegação inferior compacta (`MobileNav`) otimizada para dispositivos móveis.
* **Estados visuais de Feedback**: Componentes dedicados para telas de carregamento (`LoadingComponent`) com animações de rotação e toasts de notificação para sucesso ou falha em ações críticas.

---

## Tecnologias Utilizadas

O ecossistema do projeto foi desenvolvido utilizando as seguintes tecnologias e bibliotecas:

* **React** (com Hooks e Context API para gerenciamento de estado global)
* **TypeScript** (Garantindo tipagem estática e segurança em tempo de desenvolvimento)
* **Tailwind CSS** (Para estilização utilitária e design responsivo baseado em tokens de cores como `bg-graphite`, `text-highlight-green`, etc.)
* **React Router (v7)** (Roteamento de páginas, navegação declarativa e proteção de caminhos)
* **React Hook Form** (Manipulação de formulários de alta performance e baixo re-render)
* **Zod** (Definição de esquemas e validação de dados em runtime)
* **Lucide React** (Pacote de ícones limpos e flexíveis)
* **React Toastify** (Exibição de alertas e notificações flutuantes na tela)
* **jwt-decode** (Decodificação de payloads de tokens JWT)

---

## Estrutura de Pastas Sugerida

Com base nas importações internas dos arquivos, a estrutura arquitetural do projeto organiza-se da seguinte forma:

```text
src/
├── assets/                  # Imagens, logos e ícones vetoriais (.svg, .png)
├── components/              # Componentes genéricos e estruturais de UI
│   ├── auth/                # LoginForm, RegisterForm, GoogleLoginButton
│   ├── navigation/          # Navigation, DesktopNav, MobileNav, NavItem
│   ├── profile/             # EditProfileForm, CategorySelector
│   └── common/              # LoadingComponent
├── contexts/                # Provedores de estado global (AuthContext, DevsContext)
├── hooks/                   # Hooks customizados (useAuth, useDevs, useTokenRefresh)
├── lib/                     # Clientes HTTP e instâncias de API (fetchClient, api)
├── schemas/                 # Validações do Zod (loginSchema, registerSchema, editProfileSchema)
├── services/                # Funções de requisições à API (authService, contactService, devsService)
└── types/                   # Arquivos de definição de tipos TypeScript (.types.ts)
```
## Configuração e Instalação
Certifique-se de ter instalado em sua máquina:

Node.js (Versão LTS recomendada)

Gerenciador de pacotes npm ou yarn

Clonar o repositório:

```Bash
git clone https://github.com/seu-usuario/codeconnect.git
cd codeconnect
```
Instalar as dependências:

```Bash
npm install
```
Configurar a API:
Certifique-se de que o backend da aplicação esteja rodando na porta correta. O cliente de autenticação padrão está configurado para consumir e interagir com o endpoint local:

Base URL do Servidor: http://localhost:3001

Iniciar o servidor de desenvolvimento:

```Bash
npm run dev
```
A aplicação estará disponível no endereço indicado pelo Vite no seu terminal (geralmente http://localhost:5173).
