# Significado do Nome - Aplicação Vue.js + .NET

Esta aplicação permite descobrir o significado de nomes usando a API Gemini do Google.

## 🚀 Pré-requisitos

- [Node.js](https://nodejs.org/) (v14 ou superior)
- [.NET SDK](https://dotnet.microsoft.com/download) (9.0 )
- [Gemini](https://aistudio.google.com/) conta para obter a API Key do Gemini

## 📦 Instalação

### Backend (.NET)

1. Navegue até a pasta do backend:
```bash
cd apidotnet
```

2. Crie um arquivo `appsettings.Development.json` na pasta do projeto e adicione sua API Key do Gemini:
```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft.AspNetCore": "Warning"
    }
  },
  "AllowedHosts": "*",
  "GeminiApiKey": "SUA_API_KEY_AQUI"
}
```

3. Restaure as dependências e execute o projeto:
```bash
dotnet restore
dotnet run
```

O backend estará rodando em `http://localhost:5282`

### Frontend (Vue.js)

1. Navegue até a pasta do frontend:
```bash
cd frontend/app
```

2. Instale as dependências:
```bash
npm install
```

3. Execute o projeto:
```bash
npm run dev
```

O frontend estará disponível em `http://localhost:5173`

## 🔑 Obtendo a API Key do Gemini

1. Acesse o [Google AI Studio](https://aistudio.google.com/)
2. Faça login com sua conta Google
3. No canto superior esquerdo, selecione ou crie um novo projeto
4. No menu lateral, clique em "API Keys"
5. Clique em "Create API Key" para gerar uma nova chave
6. Copie a chave de API gerada
7. Adicione a chave no arquivo `appsettings.Development.json` do seu projeto:
```json
{
  "GeminiApiKey": "SUA_API_KEY_AQUI"
}
```

⚠️ **Importante**: 
- Nunca compartilhe sua chave de API
- Não comite o arquivo `appsettings.Development.json` no repositório
- Mantenha sua chave em um local seguro

## 🛠️ Tecnologias Utilizadas

- Frontend: Vue.js 3 + Vite + TailwindCSS
- Backend: .NET 9
- API: Google Gemini

## 👤 Autor

Arlei Junio

## 📝 Licença

Este projeto está sob a licença MIT. 
