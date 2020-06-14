# Optimus Talks - Configuração de um Guia de Estilo

## 1- O que é um Guia de Estilo?

Um guia de estilo é uma série de regras de como o código deve ser escrito, facilitando assim a interação e comunicação dos desenvolvedores, como por exemplo:

- Nome de funções;
- Identação;
- Tipo de aspa para strings;
- entre outros.

## 2- Visual Studio Code + Prettier + ESLint

- Editor de Texto: [Visual Studio Code](https://code.visualstudio.com/)

```bash
code -v
```

- Formatador do Código: [Preetier](https://prettier.io/)<br>
  `Nome da extensão para VS Code:` Prettier - Code formatter.
- Regras e Padrões do Código : [ESLint](https://eslint.org/)<br>
  `Nome da extensão para VS Code:` ESLint.

- Interpretador JavaScript: [Node.js](https://nodejs.org/en/)

```bash
node -v
```

- Gerenciador de Pacotes JavaScript: [NPM](https://www.npmjs.com/)

```bash
npm -v
```

## 3- Configuração do Ambiente

**3.1 Criar a pasta do projeto e inicializar o VS Code**

```bash
mkdir styleguide
cd styleguide
code .
```

**3.2 Criar o arquivo package.json e o arquivo .gitignore**

Abrir o `Terminal` no VS Code com o atalho `(Ctrl + ')` ou ir em `View - Terminal`

```bash
npm init -y
```

Clicar com o botão direito no explorador de arquivos no VS Code e escolher a opção `New File`, nomear o arquivo como `.gitignore`, abrir o arquivo e adicionar o seguinte conteúdo:

```plaintext
/node_modules
```

**3.3 Instalar os pacotes de desenvolvimento**

```bash
npm i -D eslint prettier eslint-plugin-prettier eslint-config-prettier eslint-plugin-node eslint-config-node
```

**3.4 Instalar o guia de estilo do Airbnb**

[eslint-config-airbnb](https://www.npmjs.com/package/eslint-config-airbnb)

```bash
npx install-peerdeps --dev eslint-config-airbnb
```

package.json

```json
  "devDependencies": {
    "eslint": "^6.8.0",
    "eslint-config-airbnb": "^18.1.0",
    "eslint-config-node": "^4.1.0",
    "eslint-config-prettier": "^6.11.0",
    "eslint-plugin-import": "^2.20.1",
    "eslint-plugin-jsx-a11y": "^6.2.3",
    "eslint-plugin-node": "^11.1.0",
    "eslint-plugin-prettier": "^3.1.3",
    "eslint-plugin-react": "^7.19.0",
    "eslint-plugin-react-hooks": "^2.5.0",
    "prettier": "^2.0.5"
  }
```

**3.5 Criar o arquivo .prettierrc**

Arquivo de configuração do Prettier.

Clicar com o botão direito no explorador de arquivos no VS Code e escolher a opção `New File`, nomear o arquivo como `.prettierrc`, abrir o arquivo e adicionar o seguinte conteúdo:

```json
{
	"singleQuote": true,
	"useTabs": true,
	"endOfLine": "auto"
}
```

As configurações podem ser feitas em arquivos locais ou globalmente para este exemplo vamos somente utilizar a opção single quote, mais opções podem ser encontradas em [Prettier Options](https://prettier.io/docs/en/options.html).

Para criar configurações globais deve-se acessar o arquivo de preferências do VS Code através do comando `(Ctrl + ,)` para visualizar as configurações ou `(Ctrl + Shift + P)` e procurar
por `Settings (JSON)`.

Algumas configurações interessantes são:

```json
{
	"editor.formatOnSave": true
}
```

**3.6 Criar o arquivo .eslintrc.json**

Arquivo de configuração do EsLint.

Clicar com o botão direito no explorador de arquivos no VS Code e escolher a opção `New File`, nomear o arquivo como `.eslintrc.json`, abrir o arquivo e adicionar o seguinte conteúdo:

```json
{
	"extends": ["airbnb", "prettier"],
	"plugins": ["prettier"],
	"rules": {
		"prettier/prettier": "error",
		"no-unused-vars": "warn",
		"no-console": "off",
		"func-names": "off",
		"object-shorthand": "off"
	}
}
```

Mais regras podem ser encontradas em [ESLint Rules](https://eslint.org/docs/rules/).

## 4- Configuração do Ambiente (Formas Alternativas)

**4.1 Alternativa para o item - 3.3 Instalar os pacotes de desenvolvimento**

```bash
npm i -D eslint
npx eslint --init
```

O terminal irá apresentar um questionário de configuração do ESLint, o mesmo deve ser respondido conforme as configurações e finalidade do projeto, assim o arquivo .eslintrc.json é criado automaticamente.

Exemplo:

- How would you like to use ESLint?
  - To check syntax, find problems, and enforce code style
- What type of modules does your project use?
  - JavaScript modules (import/export)
- Which framework does your project use?
  - None of these
- Does your project use TypeScript?
  - n
- Where does your code run?
  - Browser
- How would you like to define a style for your project?
  - Use a popular style guide
- Which style guide do you want to follow?
  - Airbnb: https://github.com/airbnb/javascript
- What format do you want your config file to be in?
  - JSON

Conforme a configuração selecionada será necessário instalar alguns pacotes, assim é preciso confirmar a instalação com y seguido de enter.

**4.2 Alternativa criar o arquivo .editorconfig**

Outra alternativa para uma configuração simples para trabalhos em equipe é criar um arquivo `.editorconfig` que pode ser utilizado em diferentes editores de texto.

- Definir Estilo do Código em Diferentes Editores: [EditorConfig](https://editorconfig.org/)<br>
  `Nome da extensão para VS Code:` EditorConfig for VS Code.

Clicar com o botão direito no explorador de arquivos no VS Code e escolher a opção `New File`, nomear o arquivo como `.editorconfig` ou clicar com o botão direto e escolher a opção `Generate .editorconfig` em seguida abrir o arquivo e adicionar o seguinte conteúdo:

```plaintext
root = true

[*]
indent_style = space
indent_size = 2
end_of_line = lf
charset = utf-8
trim_trailing_whitespace = true
insert_final_newline = true
```

## 5- Configuração do Ambiente (Exemplos)

[React](https://github.com/DiegoGeoDev/styleGuideReact)

[Node](https://github.com/DiegoGeoDev/styleGuideNode)
