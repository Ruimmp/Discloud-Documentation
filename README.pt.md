# 📚 Discloud Docs

<div align="center">
  <img src="https://i.imgur.com/za9JTHz.png" alt="Discloud Logo" width="150">
</div>

<p align="center">
  <a href="https://github.com/discloud/docs">
    <img src="https://img.shields.io/badge/GitHub-Repository-blue?style=flat-square&amp;logo=github" alt="GitHub">
  </a>
  <a href="https://docs.discloud.com">
    <img src="https://img.shields.io/badge/Documenta%C3%A7%C3%A3o-Discloud-blue?style=flat-square&amp;logo=read-the-docs" alt="Documentação">
  </a>
</p>

## 🚀 Introdução

Este repositório mantém documentação oficial da **Discloud**.

### 📚 Idiomas

- 🇬🇧 **English** – [Read the English version](README.md)

## 🗂️ Branches da documentação

As páginas ficam divididas em três branches para que cada idioma mantenha a própria árvore completa:

- `portuguese` – agrupa toda a documentação em português (`https://docs.discloud.com`).
- `english` – agrupa toda a documentação em inglês (`https://docs.discloud.com/en`).

## 📘 Regras de slug e roteamento

Os slugs (permalinks) devem continuar em inglês para manter links estáveis entre idiomas, bookmarks funcionais e integrações com automações. O slug é a parte após o domínio (por exemplo, `/getting-started/install`).

### 📝 Como organizar slugs no Markdown

Como grande parte do trabalho ocorre em Markdown, o slug depende da forma como o `SUMMARY.md` é estruturado:

1. Defina o título do grupo ou página principal.
2. Quando preciso, adicione um âncora HTML para garantir que o slug publicado seja igual ao título.
3. Liste cada página em inglês; o caminho e o nome do arquivo ditam o slug final.

Exemplo de trecho em `SUMMARY.md`:

```markdown
## How to Host Using <a href="#how-to-host-using" id="how-to-host-using"></a>

- [Control Panel](how-to-host-using/dashboard.md)
```

O vínculo acima gera `https://docs.discloud.com/how-to-host-using/dashboard`, por isso a localização do arquivo, seu nome em inglês e o âncora devem seguir o slug oficial.

### 🧭 Boas práticas para slugs

- Deixe cada slug em inglês, sem acentos, espaços ou barras finais.
- Prefira kebab-case (`how-to-host-using`) para manter URLs limpas.
- Não traduza nem altere slugs entre idiomas — apenas o conteúdo muda.
- Avalie impactos de SEO ou links existentes antes de renomear rotas; coordene qualquer mudança com a equipe.

## 🌐 Precisa confirmar algo em inglês?

Abra `README.md` para consultar o guia oficial em inglês e manter os slugs sincronizados entre as línguas.

---

<p align="center">Made with ❤️ by the Discloud Team</p>
