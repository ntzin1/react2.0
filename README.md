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
