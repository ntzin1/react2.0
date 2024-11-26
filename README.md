# React Components: Props (Aula 10)

## `MenuComponent.js`

### 1. Quais os imports utilizados? 
- **`React` e `useState`**:
  - **`React`**: Biblioteca principal para criar componentes.
  - **`useState`**: Hook para gerenciar o estado do componente (exemplo: prato selecionado).
  
- **Componentes do `reactstrap`**:
  - **`Card`, `CardImg`, `CardImgOverlay`, `CardText`, `CardBody`, `CardTitle`**:
    - Usados para exibir os pratos em cartões, com imagens, nomes e descrições.

### 2. Há componentes? O que fazem?
- **`Card`**: Exibe cada prato em formato de cartão.
- **`CardImg`**: Exibe a imagem do prato dentro do cartão.
- **`CardImgOverlay`**: Exibe o nome do prato sobre a imagem.
- **`CardBody`**: Contém o nome e descrição do prato.
- **`CardTitle` e `CardText`**: Exibem o nome e descrição do prato dentro do corpo do cartão.

### 3. Para que serve o `onDishSelect` no projeto?
- **`onDishSelect`**: Função que altera o prato selecionado. Quando o usuário clica em um prato, essa função atualiza o estado e exibe os detalhes do prato selecionado.

### 4. Para que serve o `renderDish`?
- **`renderDish`**: Exibe as informações do prato selecionado, como imagem e descrição. Se nenhum prato for selecionado, retorna um elemento vazio.

### 5. Para que serve o `props.dishes.map`?
- **`props.dishes.map`**: Método que percorre a lista de pratos passada como `props` e gera um cartão para cada prato. Exibe as imagens e nomes dos pratos dinamicamente.

---

## `dishes.js`

### O que é `dishes.js`?
- O arquivo `dishes.js` contém a lista de pratos (`DISHES`), com dados como nome, imagem, preço, descrição e comentários dos usuários. Ele serve como fonte de dados para outros componentes, como o componente `Menu`.

### Propriedades dos Objetos em `DISHES`:
- **`id`**: Identificador único (número).
- **`name`**: Nome do prato (texto).
- **`image`**: Caminho da imagem do prato (texto).
- **`category`**: Categoria do prato, como "mains" ou "dessert" (texto).
- **`label`**: Rótulo opcional, como "Hot" ou "New" (texto).
- **`price`**: Preço do prato (texto).
- **`description`**: Descrição do prato (texto).
- **`comments`**: Lista de comentários, cada comentário possui:
  - **`id`**: Identificador do comentário.
  - **`rating`**: Avaliação (número de 1 a 5).
  - **`comment`**: Texto do comentário.
  - **`author`**: Nome do autor do comentário.
  - **`date`**: Data do comentário.

### Tipos de Dados Utilizados:
- **`id`**: Número inteiro.
- **`name`, `category`, `label`, `image`, `description`, `comment`, `author`**: Texto (strings).
- **`price`**: Texto (valor monetário).
- **`rating`**: Número inteiro.
- **`comments`**: Array de objetos.

---

## `App.js`

### Para que serve o `const [dishes]`?
- **`const [dishes]`**: Usando o hook `useState`, o estado `dishes` é criado e inicializado com os dados do arquivo `dishes.js`. Isso armazena a lista de pratos na aplicação.

### Explicar como funciona o `<Menu dishes={dishes} />`
- **`<Menu dishes={dishes} />`**: Aqui, o estado `dishes` é passado para o componente `Menu` como uma propriedade (`prop`). Dentro do `Menu`, a lista de pratos pode ser acessada via `props.dishes` e usada para exibir os pratos no menu.

- Navbar dark color="primary">: Cria uma barra de navegação (navbar) com fundo escuro (dark) e a cor azul padrão (primary).

- NavbarBrand href="/">Ristorante Con Fusion /NavbarBrand>: Exibe o nome "Ristorante Con Fusion" na navbar e 
faz com que o clique no nome redirecione para a página inicial (href="/").

- div>Aluno: Sergio Rennan /div>: Exibe o texto "Aluno: Sergio Rennan" abaixo da navbar.

- Como pode ser usado:
Este código cria uma página simples com uma barra de navegação na parte superior e o nome "Aluno: Sergio Rennan" logo abaixo dela. 
É uma base que você pode expandir para adicionar mais seções ou funcionalidades ao seu site ou aplicação.
 

![IMAGEM DO RESUTADO](<WhatsApp Image 2024-11-21 at 19.54.36.jpeg>)



## components

#### **Estrutura e Blocos de Código**

##### 1. **Importação de Bibliotecas e Dependências**
```javascript
import React, { useState } from 'react';
import { Media } from 'reactstrap';
```
- **React**: Biblioteca base para criar componentes e gerenciar o estado do aplicativo.
- **useState**: Hook para gerenciar o estado do componente.
- **reactstrap**: Biblioteca de componentes React para Bootstrap, utilizada para criar layouts responsivos.

---

##### 2. **Definição do Estado e Dados**
```javascript
const [dishes] = useState([
  {
    id: 0,
    name: 'Uthappizza',
    image: 'assets/images/uthappizza.png',
    category: 'mains',
    label: 'Hot',
    price: '4.99',
    description: 'A unique combination of Indian Uthappam (pancake) and Italian pizza, topped with Cerignola olives, ripe vine cherry tomatoes, Vidalia onion, Guntur chillies and Buffalo Paneer.',
  },
  {
    id: 1,
    name: 'Zucchipakoda',
    image: 'assets/images/zucchipakoda.png',
    category: 'appetizer',
    label: '',
    price: '1.99',
    description: 'Deep fried Zucchini coated with mildly spiced Chickpea flour batter accompanied with a sweet-tangy tamarind sauce',
  },
  {
    id: 2,
    name: 'Vadonut',
    image: 'assets/images/vadonut.png',
    category: 'appetizer',
    label: 'New',
    price: '1.99',
    description: 'A quintessential ConFusion experience, is it a vada or is it a donut?',
  },
  {
    id: 3,
    name: 'ElaiCheese Cake',
    image: 'assets/images/elaicheesecake.png',
    category: 'dessert',
    label: '',
    price: '2.99',
    description: 'A delectable, semi-sweet New York Style Cheese Cake, with Graham cracker crust and spiced with Indian cardamoms.',
  },
]);
```
- **dishes**: Estado que contém um array de objetos, onde cada objeto representa um prato.
  - `id`: Identificador único do prato.
  - `name`: Nome do prato.
  - `image`: Caminho para o arquivo de imagem associado ao prato.
  - `category`: Categoria do prato (e.g., entrada, sobremesa).
  - `label`: Rotulagem opcional para destacar o prato.
  - `price`: Preço do prato.
  - `description`: Breve descrição do prato.

---

##### 3. **Mapeamento dos Pratos**
```javascript
const menu = dishes.map((dish) => {
  return (
    <div key={dish.id} className="col-12 mt-5">
      <Media tag="li">
        <Media left middle>
          <Media object src={dish.image} alt={dish.name} />
        </Media>
        <Media body className="ml-5">
          <Media heading>{dish.name}</Media>
          <p>{dish.description}</p>
        </Media>
      </Media>
    </div>
  );
});
```
- **`dishes.map`**: Itera sobre o array de pratos (`dishes`), retorn
# Getting Started with Create React App

This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app).

## Available Scripts

In the project directory, you can run:

### `npm start`

Runs the app in the development mode.\
Open [http://localhost:3000](http://localhost:3000) to view it in your browser.

The page will reload when you make changes.\
You may also see any lint errors in the console.

### `npm test`

Launches the test runner in the interactive watch mode.\
See the section about [running tests](https://facebook.github.io/create-react-app/docs/running-tests) for more information.

### `npm run build`

Builds the app for production to the `build` folder.\
It correctly bundles React in production mode and optimizes the build for the best performance.

The build is minified and the filenames include the hashes.\
Your app is ready to be deployed!

See the section about [deployment](https://facebook.github.io/create-react-app/docs/deployment) for more information.

### `npm run eject`

**Note: this is a one-way operation. Once you `eject`, you can't go back!**

If you aren't satisfied with the build tool and configuration choices, you can `eject` at any time. This command will remove the single build dependency from your project.

Instead, it will copy all the configuration files and the transitive dependencies (webpack, Babel, ESLint, etc) right into your project so you have full control over them. All of the commands except `eject` will still work, but they will point to the copied scripts so you can tweak them. At this point you're on your own.

You don't have to ever use `eject`. The curated feature set is suitable for small and middle deployments, and you shouldn't feel obligated to use this feature. However we understand that this tool wouldn't be useful if you couldn't customize it when you are ready for it.

## Learn More

You can learn more in the [Create React App documentation](https://facebook.github.io/create-react-app/docs/getting-started).

To learn React, check out the [React documentation](https://reactjs.org/).

### Code Splitting

This section has moved here: [https://facebook.github.io/create-react-app/docs/code-splitting](https://facebook.github.io/create-react-app/docs/code-splitting)

### Analyzing the Bundle Size

This section has moved here: [https://facebook.github.io/create-react-app/docs/analyzing-the-bundle-size](https://facebook.github.io/create-react-app/docs/analyzing-the-bundle-size)

### Making a Progressive Web App

This section has moved here: [https://facebook.github.io/create-react-app/docs/making-a-progressive-web-app](https://facebook.github.io/create-react-app/docs/making-a-progressive-web-app)

### Advanced Configuration

This section has moved here: [https://facebook.github.io/create-react-app/docs/advanced-configuration](https://facebook.github.io/create-react-app/docs/advanced-configuration)

### Deployment

This section has moved here: [https://facebook.github.io/create-react-app/docs/deployment](https://facebook.github.io/create-react-app/docs/deployment)

### `npm run build` fails to minify

This section has moved here: [https://facebook.github.io/create-react-app/docs/troubleshooting#npm-run-build-fails-to-minify](https://facebook.github.io/create-react-app/docs/troubleshooting#npm-run-build-fails-to-minify)
