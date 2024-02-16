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

### O que é o Jekyll?

Jekyll é um gerador de sites estáticos escrito em Ruby. Ele transforma conteúdo escrito em Markdown, HTML e YAML em um site estático completo, pronto para ser servido na web. Uma das principais vantagens do Jekyll é sua simplicidade e eficiência, permitindo que desenvolvedores construam e publiquem sites rapidamente, sem a necessidade de um banco de dados ou servidor dinâmico.

### Como o Jekyll funciona?

O Jekyll funciona convertendo arquivos de texto simples em um site estático. Ele utiliza um processo de compilação onde os arquivos de entrada, como Markdown, HTML, YAML, etc., são processados por meio de modelos e layouts para gerar páginas HTML completas. Durante esse processo, o Jekyll também permite a organização automática de conteúdo, como posts de blog, através do uso de diretórios e convenções de nomenclatura.

### Principais recursos do Jekyll:

#### 1. Simplicidade:
    - Não há necessidade de um servidor dinâmico.
    - Desenvolvimento e manutenção simplificados com arquivos de texto simples.

#### 2. Flexibilidade:
    - Suporte para layouts e templates reutilizáveis.
    - Integração com Sass, CoffeeScript e outras ferramentas populares.

#### 3. Personalização:
    - Capacidade de criar plugins personalizados para estender funcionalidades.
    - Configuração flexível por meio de arquivos de configuração YAML.

#### 4. Integração com o GitHub Pages:
    - Fácil publicação de sites Jekyll usando o GitHub Pages.

### Workflow do Jekyll:

1. **Instalação:**
   - Instale o Jekyll em sua máquina seguindo as instruções na documentação oficial. Veja o próximo capítulo para mais detalhes.

2. **Estrutura do projeto:**
   - Organize seus arquivos conforme as convenções do Jekyll, como diretórios para layouts, includes, posts, etc.

3. **Configuração:**
   - Configure seu site editando o arquivo `_config.yml`, onde você pode definir variáveis, ajustar configurações e muito mais.

4. **Desenvolvimento:**
   - Escreva seu conteúdo em Markdown ou HTML e utilize os layouts e includes para estruturar seu site.

5. **Compilação e visualização:**
   - Execute o comando `bundle exec jekyll serve` em seu terminal para compilar e visualizar seu site localmente.

6. **Publicação:**
   - Após realizar alterações, faça o push do código para um repositório no GitHub e habilite o GitHub Pages para publicar seu site online.

## Instalando o Código Localmente

Jekyll é uma Gem de Ruby, e pode ser instalado na maioria dos sistemas. Como há constantes atualizações no sistema, é melhor seguir o guia mais atualizado em: [Guia de Instalação](https://jekyllrb.com/docs/installation/).

Caso haja problemas de compatibilidade, o site foi desenvolvido nas seguintes versões:

`Jekyll: v4.3.3`

`Ruby: v3.3.0`

## Manutenções Futuras

Irei falar agora sobre manutenções e modificaçoes estéticas que possam vir a ser necessárias. O Jekyll funciona com temas, eles facilitam o desenvolvimento pois possuem inúmeros layouts prontos que otimizam a experiência do desenvolvedor. Entretanto, esses layouts podem ser alterados para personalizar ainda mais o site. O tema utilizado nesse site foi o [MMistakes](https://github.com/mmistakes/minimal-mistakes), ao entrar no github dele você encontra o código fonte de todos os layouts na página _layouts.

### Personalizando Layouts:

Caso queira modificar os layouts, como por exemplo alterar a posição dos posts na home page, crie um diretório chamado _layouts e nele adicione `home.html`, em seguida copie o `home.html` da pasta layouts do github do [MMistakes](https://github.com/mmistakes/minimal-mistakes). O arquivo é algo como:

```
---
layout: archive
---

{{ content }}

<h3 class="archive__subtitle">{{ site.data.ui-text[site.locale].recent_posts | default: "Recent Posts" }}</h3>

{% if paginator %}
  {% assign posts = paginator.posts %}
{% else %}
  {% assign posts = site.posts %}
{% endif %}

{% assign entries_layout = page.entries_layout | default: 'list' %}
<div class="entries-{{ entries_layout }}">
  {% for post in posts %}
    {% include archive-single.html type=entries_layout %}
  {% endfor %}
</div>

{% include paginator.html %}
```

Digamos que eu queira que primeiro sejam colocados os posts e depois as informações do arquivo index.html, o arquivo `home.html` ficaria algo assim:

```
---
layout: archive
---

<h3 class="archive__subtitle">{{ site.data.ui-text[site.locale].recent_posts | default: "Recent Posts" }}</h3>

{% if paginator %}
  {% assign posts = paginator.posts %}
{% else %}
  {% assign posts = site.posts %}
{% endif %}

{% assign entries_layout = page.entries_layout | default: 'list' %}
<div class="entries-{{ entries_layout }}">
  {% for post in posts %}
    {% include archive-single.html type=entries_layout %}
  {% endfor %}
</div>

{% include paginator.html %}

{{ content }}
```

Isso se aplica a outros layouts também. Para entender todos os layouts do [MMistakes](https://github.com/mmistakes/minimal-mistakes), sugiro seguir o tutorial deles em [Quick-Start Guide](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/)
