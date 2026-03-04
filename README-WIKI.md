# 🚀 Como Publicar o Wiki no GitHub

Este diretório contém todos os arquivos do Wiki do Baiten ANC.

---

## 📋 Passos para Publicar

### 1. Ative o Wiki no GitHub

1. Acesse: https://github.com/dkamioka/BaitenANC-backend
2. Clique na aba **"Settings"** (Configurações)
3. No menu lateral, clique em **"Pages"** ou vá direto para:  
   https://github.com/dkamioka/BaitenANC-backend/settings/pages
4. Na seção **"Wiki"**, marque a opção **"Enable Wikis"**

### 2. Clone o Repositório Wiki

Após ativar, execute:

```bash
# Clone o wiki (URL diferente)
git clone https://github.com/dkamioka/BaitenANC-backend.wiki.git

# Entre no diretório
cd BaitenANC-backend.wiki
```

### 3. Copie os Arquivos

```bash
# Copie todos os arquivos do wiki local
cp -r /caminho/para/BaitenANC-backend/wiki/*.md .

# Ou se estiver no diretório do projeto:
cp -r ../wiki/*.md .
```

### 4. Faça o Push

```bash
# Adicione todos os arquivos
git add -A

# Commit
git commit -m "Initial wiki commit"

# Push
git push origin main
```

---

## 📁 Arquivos do Wiki

| Arquivo | Descrição |
|---------|-----------|
| `Home.md` | Página inicial do Wiki |
| `_Sidebar.md` | Menu de navegação lateral |
| `_Footer.md` | Rodapé do Wiki |
| `Manual-Completo.md` | Documentação completa |
| `Guia-Rapido.md` | Referência rápida |
| `Cartilha-Visual.md` | Exemplos visuais |
| `FAQ.md` | Perguntas frequentes |
| `Glossario.md` | Termos técnicos |
| `Tutorial-*.md` | Tutoriais passo a passo |

---

## 🌐 URL do Wiki

Após publicar, acesse:

**https://github.com/dkamioka/BaitenANC-backend/wiki**

---

## 📝 Alternativa: GitHub Pages

Se preferir usar GitHub Pages em vez de Wiki:

1. Ative GitHub Pages nas configurações
2. Use a pasta `docs/` no branch `main`
3. Mova estes arquivos para `docs/`
4. O GitHub Pages gerará um site bonito automaticamente

URL seria: **https://dkamioka.github.io/BaitenANC-backend/**

---

## ✅ Checklist

- [ ] Wiki ativado nas configurações do GitHub
- [ ] Arquivos copiados para o repositório wiki
- [ ] Push realizado
- [ ] URL acessível publicamente
- [ ] Links internos funcionando

---

*Documentação criada em Março 2025*
