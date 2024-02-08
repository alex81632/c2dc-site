# Site do Laboratório C2 do ITA

Essa documentação seguirá a seginte ordem:

1) Adicionando um Post
2) Explicação do Framework
3) Instalando o Código Localmente
4) Manutenções Futuras

## Adicionando um Post

Um Post deve ser escrito em formato `.markdown` e o seu nome deve seguir o padrão `AAAA-MM-DD-TÍTULO-COMPLETO.markdown`.

O arquivo deve começar com:

```{yml}
---

---
```

Opcionamente você pode adicionar manualmente um título e uma data caso seja necessário. Se o fizer, essas informações irão sobrescrecer as informações do nome do arquivo. A seguir temos os principais atributos que podem ser modificados:

```{yml}
---
title: Sobre Nós
date: 2023-12-15
permalink: /about/
author_profile: true
## Sobre a table of contents
toc: true
toc_label: "Capítulos"
---
```

Após esse cabeçalho, o post pode continuar a ser escrito normalmente em markdown. 

```
NOTA: caso esteja utilizando a toc, é necessário seguir a ordem de títulos no markdown para que a toc funcione corretamente. Ex:

Correto:
# Titulo 1
## SubTitulo 1
# Titulo 2
...

Errado:
# Titulo 1
### SubTitulo 1
...
```

## Explicação do Framework

## Instalando o Código Localmente

## Manutenções Futuras
