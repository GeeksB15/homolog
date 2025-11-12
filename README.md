       ______          __           _____       __            /\//          
      / ____/__  ___  / /_______   / ___/____  / /_  ________//\/ ___  _____
     / / __/ _ \/ _ \/ //_/ ___/   \__ \/ __ \/ / / / / ___/ __ \/ _ \/ ___/
    / /_/ /  __/  __/ ,< (__  )   ___/ / /_/ / / /_/ / /__/ /_/ /  __(__  ) 
    \____/\___/\___/_/|_/____/   /____/\____/_/\__,_/\___/\____/\___/____/  
                                                     /_)                    

# 🧠 Geeks Soluções — B15 App + Homolog Deploy

Este projeto faz parte do **ecossistema B-15**, composto por dois repositórios principais:

- **B15App** → Aplicação Quasar Framework (frontend principal)
- **homolog** → Ambiente de homologação hospedado no **GitHub Pages**

O fluxo de publicação automatizado permite gerar versões de homologação isoladas, acessíveis via  
👉 **https://geeksb15.github.io/homolog**

Cada versão de build é armazenada em uma subpasta do repositório `homolog`, ex:  
```
/homolog/2025/
/homolog/2026/
```

O `404.html` presente no `homolog` oferece uma interface moderna que permite digitar a versão desejada ou redireciona automaticamente se a rota contiver `/homolog/{versao}/...`.

---

## 🚀 Estrutura do Projeto

A árvore esperada de diretórios no mesmo nível:

```
📁 /meus-projetos/
 ├─ 📂 B15App/
 │   ├─ src/
 │   ├─ package.json
 │   └─ ...
 └─ 📂 homolog/
     ├─ 404.html
     ├─ 2025/
     └─ ...
```

> ⚠️ É **obrigatório** que os diretórios `B15App` e `homolog` estejam lado a lado,  
> pois o script de deploy copia os arquivos diretamente para a pasta do `homolog`.

---

### 📦 Deploy para Homolog

```bash
npm run deploy:homolog <versao>
```

#### Exemplo:
```bash
npm run deploy:homolog 2025
```

Este comando executa:
1. Gera o build de produção do Quasar (`dist/spa`).
2. Copia os arquivos para `../homolog/<versao>/`.
3. Realiza commit e push automáticos no repositório `homolog`.
4. Disponibiliza o build em:
   ```
   https://geeksb15.github.io/homolog/<versao>/
   ```