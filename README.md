
# 🚀 Social Network Database

Este repositório contém o script SQL e o diagrama ER para o banco de dados de uma rede social. O banco de dados foi projetado para armazenar informações de usuários, postagens, conexões entre amigos, comentários e curtidas.

---

## 📁 Estrutura do Projeto

```plaintext
social-network-db/
├── docs/               # Diagramas e documentação
│   └── diagrama.png    # Diagrama ER exportado
├── sql/                # Scripts SQL
│   └── social_network.sql # Script de criação do banco de dados
└── README.md           # Documentação do projeto
```

---

## 📝 Descrição do Banco de Dados

O banco de dados foi modelado para armazenar os seguintes dados principais:

| Tabela   | Descrição                                          |
|----------|----------------------------------------------------|
| `users`   | Armazena informações dos usuários.                 |
| `posts`   | Guarda as postagens feitas pelos usuários.          |
| `friends` | Representa conexões entre amigos na rede social.    |
| `comments`| Armazena os comentários feitos em postagens.        |
| `likes`   | Registra curtidas em postagens e comentários.       |

---

## 📊 Modelo ER (Entity Relationship)

Abaixo está o diagrama ER do banco de dados:

![Diagrama ER](./docs/diagrama.png)

---

## 🏗️ Estrutura das Tabelas

### **1. `users`**  
Armazena informações dos usuários cadastrados na rede social.

**Colunas:**
| Nome            | Tipo          | Descrição                                      |
|-----------------|---------------|------------------------------------------------|
| `user_id`        | INT (PK)       | Identificador único do usuário (autoincremento). |
| `username`        | VARCHAR(50)     | Nome de usuário.                               |
| `email`           | VARCHAR(100)    | E-mail do usuário.                             |
| `password`        | VARCHAR(100)    | Senha do usuário (criptografada).               |
| `bio`             | TEXT            | Biografia do usuário.                           |
| `profile_pic_url`  | VARCHAR(255)    | URL da foto de perfil.                          |
| `created_at`       | TIMESTAMP       | Data de criação da conta.                       |

---

### **2. `posts`**  
Guarda as postagens feitas pelos usuários.

**Colunas:**
| Nome          | Tipo          | Descrição                                        |
|---------------|---------------|--------------------------------------------------|
| `post_id`       | INT (PK)       | Identificador único da postagem (autoincremento). |
| `user_id`        | INT (FK)        | Identificador do autor da postagem.               |
| `content`         | TEXT            | Conteúdo da postagem.                             |
| `image_url`        | VARCHAR(255)    | URL da imagem na postagem (opcional).              |
| `created_at`       | TIMESTAMP       | Data de criação da postagem.                       |

**Relacionamentos:**
- `user_id` → `users.user_id`

---

### **3. `friends`**  
Armazena conexões entre amigos.

**Colunas:**
| Nome          | Tipo          | Descrição                                        |
|---------------|---------------|--------------------------------------------------|
| `friendship_id`  | INT (PK)       | Identificador único da conexão (autoincremento). |
| `user1_id`        | INT (FK)        | Identificador do primeiro usuário.               |
| `user2_id`        | INT (FK)        | Identificador do segundo usuário.                |
| `status`          | ENUM            | Status da conexão (`pending`, `accepted`, `rejected`). |
| `created_at`       | TIMESTAMP       | Data de criação da conexão.                       |

**Relacionamentos:**
- `user1_id` → `users.user_id`  
- `user2_id` → `users.user_id`  

---

### **4. `comments`**  
Armazena os comentários feitos em postagens.

**Colunas:**
| Nome          | Tipo          | Descrição                                        |
|---------------|---------------|--------------------------------------------------|
| `comment_id`     | INT (PK)       | Identificador único do comentário (autoincremento). |
| `post_id`         | INT (FK)        | Identificador da postagem comentada.              |
| `user_id`         | INT (FK)        | Identificador do autor do comentário.              |
| `content`          | TEXT            | Conteúdo do comentário.                            |
| `created_at`        | TIMESTAMP       | Data de criação do comentário.                     |

**Relacionamentos:**
- `post_id` → `posts.post_id`  
- `user_id` → `users.user_id`  

---

### **5. `likes`**  
Armazena as curtidas em postagens e comentários.

**Colunas:**
| Nome          | Tipo          | Descrição                                        |
|---------------|---------------|--------------------------------------------------|
| `like_id`         | INT (PK)       | Identificador único da curtida (autoincremento). |
| `target_id`        | INT             | ID do post ou comentário curtido.                |
| `user_id`          | INT (FK)        | Identificador do usuário que deu o like.          |
| `type`             | ENUM            | Tipo de curtida (`post` ou `comment`).             |
| `created_at`        | TIMESTAMP       | Data da curtida.                                  |

**Relacionamentos:**
- `user_id` → `users.user_id`  

---

## 🚀 Como Configurar o Banco de Dados

1. Clone o repositório:
```bash
git clone https://github.com/seu-usuario/social-network-db.git
cd social-network-db
```

2. Crie o banco de dados e execute o script:
```sql
CREATE DATABASE social_network;
USE social_network;
SOURCE ./sql/social_network.sql;
```

3. Verifique as tabelas criadas:
```sql
SHOW TABLES;
```

---

## ✅ Melhorias Futuras
- Adicionar suporte para mensagens diretas entre usuários.  
- Implementar uma funcionalidade de notificações para curtidas e comentários.  
- Criar uma tabela para armazenar imagens e vídeos de forma mais eficiente.  

---

## 🏆 Contribuição
Contribuições são bem-vindas! Sinta-se à vontade para abrir uma issue ou enviar um pull request.

---

## 📜 Licença
Este projeto está licenciado sob a **MIT License**.

---

Se precisar de mais ajustes ou quiser adicionar mais detalhes, só pedir! 😎
```
