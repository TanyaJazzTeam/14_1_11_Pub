Primeiro Cabeçalho | Segundo Cabeçalho
--- | ---
Célula de conteúdo | Célula de conteúdo
Célula de conteúdo | Célula de conteúdo

Primeiro Cabeçalho | Segundo Cabeçalho
--- | ---
Célula de conteúdo | Célula de conteúdo
Célula de conteúdo | Célula de conteúdo

![Cidadela](https://vignette.wikia.nocookie.net/masseffect/images/d/d7/MassEffect2Citadel.jpg/revision/latest?cb=20100721191415)

Esquerda alinhada | Centralizado | Alinhado à Direita
:-- | :-: | --:
coluna 3 é | algum texto prolixo | **$ 1600**
coluna 2 é | centrado | $ 12
listras de zebra | são legais | ~~$1~~

Dillinger é um editor HTML5 Markdown habilitado para nuvem, pronto para dispositivos móveis, armazenamento offline e AngularJS.

- Digite algum Markdown à esquerda
- Veja HTML à direita
- Magia

# verdadeiro

- Importe um arquivo HTML e veja-o converter magicamente para Markdown
- Arraste e solte imagens (requer que sua conta do Dropbox esteja vinculada)

Você também pode:

- Importe e salve arquivos do GitHub, Dropbox, Google Drive e One Drive
- Arraste e solte markdown e arquivos HTML no Dillinger
- Exporte documentos como Markdown, HTML e PDF

Markdown é uma linguagem de marcação leve baseada nas convenções de formatação que as pessoas usam naturalmente em emails. Como [John Gruber] escreve no [site Markdown][df1]

> O objetivo primordial do design para a sintaxe de formatação do Markdown é torná-lo o mais legível possível. A ideia é que um documento formatado em Markdown possa ser publicado como está, como texto simples, sem parecer que foi marcado com tags ou instruções de formatação.

Este texto que você vê aqui é *realmente* escrito em Markdown! Para ter uma ideia da sintaxe do Markdown, digite algum texto na janela da esquerda e observe os resultados à direita.

### falso

Dillinger usa vários projetos de código aberto para funcionar corretamente:

- [AngularJS] - HTML aprimorado para aplicativos da web!
- [Ace Editor] - incrível editor de texto baseado na web
- [markdown-it] - Analisador Markdown feito corretamente. Rápido e fácil de estender.
- [Twitter Bootstrap] - ótimo clichê de interface do usuário para aplicativos da web modernos
- [node.js] - eventos de E/S para o back-end
- [Express] - framework de aplicativo de rede node.js rápido [@tjholowaychuk]
- [Gulp] - o sistema de compilação de streaming
- [Breakdance](https://breakdance.github.io/breakdance/) - conversor de HTML para Markdown
- [jQuery] - duh

E, claro, o próprio Dillinger é de código aberto com um [repositório público][dill] no GitHub.

### Instalação

![Ilos](https://lh3.googleusercontent.com/proxy/DDV8a7sLIWurhJtW8Ego9bq-JlwpfFFoR0tkLJQKKYXEXoWHB6ZUP5jGKD2VcYt3z1QVsgcn6L3GoU1ns8m9fvi3U51GzddA70ZUMHgzHvjl4-i7YOJY9cShBPrfjUhMQhxaJ97WFBp612XmjMXVGypfGkiBarN4PWxhiHkiYYNW7HGbtTpOcyt9GQ4Q23C2noxLTWFXZMcQZhRpQA_qzu2n6_H6CPViBnhSHpEl4JZAPaGCSJqgZg)

Dillinger requer [Node.js](https://nodejs.org/) v4+ para rodar.

Instale as dependências e devDependencies e inicie o servidor.

```sh
$ cd dillinger
$ npm install -d
$ node app
```

Para ambientes de produção...

```sh
$ npm install --production
$ NODE_ENV=production node app
```

### Plugins

Dillinger está atualmente estendido com os seguintes plugins. Instruções sobre como usá-los em seu próprio aplicativo estão no link abaixo.

Plugar | Leia-me
--- | ---
Dropbox | [plugins/dropbox/README.md][PlDb]
GitHub | [plugins/github/README.md][PlGh]
Google Drive | [plugins/googledrive/README.md][PlGd]
OneDrive | [plugins/onedrive/README.md][PlOd]
Médio | [plugins/medium/README.md][PlMe]
Google Analytics | [plugins/googleanalytics/README.md][PlGa]

### Desenvolvimento

## alternativo

As métricas que compõem o Core Web Vitals [evoluirão](#evolving-web-vitals) com o tempo. O conjunto atual para 2020 se concentra em três aspectos da experiência do usuário — *carregamento* , *interatividade* e *estabilidade visual* — e inclui as seguintes métricas

Quer contribuir? Excelente!

Dillinger usa Gulp + Webpack para desenvolvimento rápido. Faça uma alteração em seu arquivo e veja instantaneamente suas atualizações!

Abra seu Terminal favorito e execute estes comandos.

Primeira guia:

```sh
$ node app
```

Segunda aba:

```sh
$ gulp watch
```

(opcional) Terceiro:

```sh
$ karma test
```

#### Construção para fonte

Para liberação de produção:

```sh
$ gulp build --prod
```

Gerando arquivos zip pré-construídos para distribuição:

```sh
$ gulp build dist --prod
```

### Docker

O Dillinger é muito fácil de instalar e implantar em um contêiner Docker.

Por padrão, o Docker exporá a porta 8080, portanto, altere isso no Dockerfile, se necessário. Quando estiver pronto, basta usar o Dockerfile para criar a imagem.

```sh
cd dillinger
docker build -t joemccann/dillinger:${package.json.version} .
```

Isso criará a imagem do dillinger e extrairá as dependências necessárias. Certifique-se de trocar `${package.json.version}` pela versão real do Dillinger.

Feito isso, execute a imagem do Docker e mapeie a porta para o que você desejar em seu host. Neste exemplo, simplesmente mapeamos a porta 8000 do host para a porta 8080 do Docker (ou qualquer porta exposta no Dockerfile):

```sh
docker run -d -p 8000:8080 --restart="always" <youruser>/dillinger:${package.json.version}
```

Verifique a implantação navegando até o endereço do servidor em seu navegador preferido.

```sh
127.0.0.1:8000
```

#### Kubernetes + Google Cloud

Consulte [KUBERNETES.md](https://github.com/joemccann/dillinger/blob/master/KUBERNETES.md)

### Todos
