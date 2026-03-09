# 💝 Lista de Desejos — Madu & Gugs

Site de lista de desejos compartilhada em tempo real, hospedado no **GitHub Pages** com banco de dados no **Firebase** (tudo gratuito).

---

## 🚀 Como colocar no ar (passo a passo)

### PARTE 1 — Criar o banco de dados no Firebase

1. Acesse [console.firebase.google.com](https://console.firebase.google.com) e faça login com sua conta Google.

2. Clique em **"Adicionar projeto"** → dê um nome (ex: `lista-desejos-madu-gugs`) → desative o Google Analytics (não precisa) → **Criar projeto**.

3. No menu lateral, clique em **"Realtime Database"** → **"Criar banco de dados"**.

4. Escolha a localização **us-central1** (ou qualquer uma) → selecione **"Iniciar no modo de teste"** → **Ativar**.
   > ⚠️ Modo de teste permite leitura/escrita pública por 30 dias. Depois veja a seção "Segurança" abaixo.

5. No menu lateral, clique no ícone de engrenagem ⚙️ → **"Configurações do projeto"**.

6. Role até **"Seus aplicativos"** → clique no ícone `</>` (Web) → dê um apelido → **Registrar app**.

7. Você verá um bloco de código assim:
   ```js
   const firebaseConfig = {
     apiKey: "AIza...",
     authDomain: "seu-projeto.firebaseapp.com",
     databaseURL: "https://seu-projeto-default-rtdb.firebaseio.com",
     projectId: "seu-projeto",
     storageBucket: "seu-projeto.appspot.com",
     messagingSenderId: "123456789",
     appId: "1:123..."
   };
   ```
   **Copie esses valores** — você vai precisar no próximo passo.

---

### PARTE 2 — Configurar o código

1. Abra o arquivo `index.html` neste projeto.

2. Procure o trecho (por volta da linha 20):
   ```js
   const firebaseConfig = {
     apiKey: "COLE_AQUI",
     ...
   };
   ```

3. **Substitua cada `"COLE_AQUI"`** pelo valor correspondente do Firebase.

4. Salve o arquivo.

---

### PARTE 3 — Subir no GitHub Pages

1. Crie um repositório no GitHub (pode ser público ou privado).
   > Repositório privado com GitHub Pages requer plano pago. Use **público** para ficar 100% free.

2. Suba os arquivos:
   ```bash
   git init
   git add .
   git commit -m "primeira versão da lista de desejos ♡"
   git branch -M main
   git remote add origin https://github.com/SEU_USUARIO/SEU_REPO.git
   git push -u origin main
   ```

3. No repositório do GitHub → **Settings** → **Pages** → Source: `Deploy from branch` → Branch: `main` → pasta: `/ (root)` → **Save**.

4. Aguarde ~1 minuto. O site estará em: `https://SEU_USUARIO.github.io/SEU_REPO/`

5. **Salve esse link nos favoritos** do celular de vocês dois! 📱

---

## 🔒 Segurança (recomendado após configurar)

Depois de testar, atualize as regras do Firebase para evitar abuso.

No Firebase Console → Realtime Database → **Regras**, cole:

```json
{
  "rules": {
    "wishlist": {
      ".read": true,
      ".write": true
    }
  }
}
```

Isso mantém acesso público ao path `wishlist` — suficiente para o uso de vocês dois. Se quiser mais segurança no futuro, implemente autenticação.

---

## ✨ Funcionalidades

- ✅ Lista separada por pessoa (Madu 🌸 e Gugs ⚡)
- ✅ Sincronização em **tempo real** — mudanças aparecem instantaneamente
- ✅ Marcar itens como realizados
- ✅ Adicionar novos desejos com nome e valor
- ✅ Remover itens
- ✅ Filtrar por pendentes / realizados
- ✅ Barra de progresso
- ✅ Funciona no celular e no PC

---

## 🔄 Como atualizar o site depois

Sempre que editar o `index.html`, basta fazer:

```bash
git add .
git commit -m "atualização"
git push
```

O GitHub Pages atualiza automaticamente em ~1 minuto.
