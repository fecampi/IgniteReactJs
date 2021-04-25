### Configurando


Inicializando o Projeto;
```jsx
yarn init -y
```

Instalando o React;
```jsx
yarn add react
```

Instalando o React-DOM (conversar com a arvore de elementos do HTML);
```jsx
yarn add react-dom
```

Instalando o Babel (converter o código para todos os navegadores);
```jsx
yarn add @babel/core @babel/cli @babel/preset-env  @babel/preset-react -D
```

Instalando o webpack;
```jsx
yarn add webpack webpack-cli babel-loader webpack-dev-server -D
```

Variáveis de ambiente;
```jsx
yarn add cross-env -D
```

Ferramentas para manipular o css;
```jsx
yarn add style-loader css-loader sass-loader node-sass -D
```

Configuração do babel.config.js;
```jsx
module.exports = {
  presets: [
    "@babel/preset-env",
    ["@babel/preset-react", { runtime: "automatic" }],
  ],
};
```

Configuração do webpack.config.js.
```jsx
const path = require("path");
const HtmlWebpackPlugin = require("html-webpack-plugin");

const isDevelopment = process.env.NODE_ENV !== "production";

module.exports = {
  mode: isDevelopment ? "development" : "production",
  devtool: isDevelopment ? "eval-source-map" : "source-map",
  entry: path.resolve(__dirname, "src", "index.jsx"),
  output: {
    path: path.resolve(__dirname, "dist"),
    filename: "bundle.js",
  },
  resolve: {
    extensions: [".js", ".jsx"],
  },
  plugins: [
    new HtmlWebpackPlugin({
      template: path.resolve(__dirname, "public", "index.html"),
    }),
  ],
  devServer: {
    contentBase: path.resolve(__dirname, "public"),
  },
  module: {
    rules: [
      {
        test: /\.jsx$/,
        exclude: /node_modules/,
        use: "babel-loader",
      },
      {
        test: /\.scss$/,
        exclude: /node_modules/,
        use: ["style-loader",'css-loader','sass-loader'],
      },
    ],
  },
};

```
