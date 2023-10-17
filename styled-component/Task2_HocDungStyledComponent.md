# Styled-Component

## Ưu điểm và nhược điểm khi sử dụng

### Ưu điểm

- Tích hợp CSS và Components: Styled-components cho phép bạn viết CSS dựa trên các components của React, giúp tạo ra các components được tùy chỉnh với các kiểu CSS riêng biệt.

- Dynamic Styling: Bạn có thể dễ dàng thay đổi kiểu CSS của một component dựa trên các props hoặc trạng thái của component.

- Scoped Styles: Kiểu CSS chỉ áp dụng cho component cụ thể, giúp tránh xung đột với các styles ở các components khác.

- Thừa kế Props: Các props có thể được chuyển đến các styled-components, giúp việc tạo ra các biến thể của components dễ dàng.

- Tích hợp với Theming: Styled-components hỗ trợ các chủ đề (themes) giúp bạn quản lý kiểu CSS trong ứng dụng của mình dễ dàng hơn

### Nhược điểm

- Learning Curve: Đối với những người mới học React, việc học cách sử dụng styled-components có thể mất một thời gian để hiểu cách nó hoạt động và cách tích hợp nó vào ứng dụng.

- Performance Overheads: Mặc dù đã có nhiều cải tiến về hiệu suất, việc chuyển đổi CSS thành các styled-components có thể tạo ra một số overhead nhỏ về hiệu suất.

```
npm install styled-components
# hoặc
yarn add styled-components
```

- Để sử dụng nó ở các file mà chúng ta cần sử dụng thì sử dụng câu lệnh sau để import.

```js
import styled from "styled-components";
```

## các cách sử dụng Styled-component

### 1. Tích hợp CSS vào Component

- Styled-components cho phép viết CSS dựa trên các components của React. Dưới đây là một ví dụ về cách tạo một component ProductCard và áp dụng kiểu CSS cho nó:

```js
import React from "react";
import styled from "styled-components";

const ProductCardWrapper = styled.div`
  border: 1px solid #ccc;
  padding: 16px;
  margin: 8px;
`;

const ProductTitle = styled.h2`
  font-size: 18px;
  margin-bottom: 8px;
`;

const ProductPrice = styled.p`
  font-size: 16px;
  color: green;
`;

const ProductCard = ({ title, price }) => {
  return (
    <ProductCardWrapper>
      <ProductTitle>{title}</ProductTitle>
      <ProductPrice>${price}</ProductPrice>
    </ProductCardWrapper>
  );
};

export default ProductCard;
```

## 2. Adapting based on props

- Bạn có thể thay đổi giao diện của component dựa trên các props mà bạn có thể truyền vào nó. Trong react, các component thường nhận vào các props ttuwf component cha truyền xuống và giúp tái sử dụng được các component.

```js
import React from "react";
import styled from "styled-components";

const Button = styled.button`
  padding: 10px 20px;
  border: none;
  border-radius: 5px;
  font-size: 16px;
  cursor: pointer;

  background-color: ${(props) =>
    props.variant === "primary" ? "blue" : "gray"};
  color: ${(props) => (props.variant === "primary" ? "white" : "black")};

  &:hover {
    background-color: ${(props) =>
      props.variant === "primary" ? "darkblue" : "lightgray"};
  }
`;

const MyComponent = () => {
  return (
    <div>
      <Button variant="primary">Primary Button</Button>
      <Button variant="secondary">Secondary Button</Button>
    </div>
  );
};

export default MyComponent;
```

## Extending styles

- Khi bạn muốn tạo một styled-component mới dựa trên một styled-component đã tồn tại và chỉ muốn điều chỉnh một số thuộc tính kiểu CSS mà không muốn viết lại từ đầu, bạn có thể sử dụng tính năng "extending styles" trong styled-components.

```js
import styled from "styled-components";

const Button = styled.button`
  background-color: blue;
  color: white;
  padding: 10px 20px;
  border: none;
  border-radius: 5px;

  &:hover {
    background-color: darkblue;
  }
`;

export default Button;
```

```js
import styled from "styled-components";
import Button from "./Button"; // Import styled-component Button

const RedButton = styled(Button)`
  background-color: red;
  &:hover {
    background-color: darkred;
  }
`;

export default RedButton;
```

## Global Styles

- Trong styled-components, bạn có thể sử dụng "createGlobalStyle" để tạo các kiểu CSS toàn cầu (global styles) cho ứng dụng của bạn. Global styles là những kiểu CSS được áp dụng cho tất cả các phần tử trong ứng dụng của bạn, không chỉ riêng cho các components.

```js
import { createGlobalStyle } from "styled-components";

const GlobalStyle = createGlobalStyle`
  body {
    font-family: 'Arial', sans-serif;
    color: #333;
  }

  h1 {
    font-size: 24px;
    color: blue;
  }
`;

const App = () => (
  <>
    <GlobalStyle />
    <h1>Hello world!</h1>
    <p>Some text here.</p>
  </>
);
```

## Animation

- Trong Styled Components, bạn có thể sử dụng CSS animation để tạo hiệu ứng chuyển động cho các thành phần. Để làm điều này, bạn có thể sử dụng thuộc tính animation trong CSS.

```js
// Create the keyframes
const rotate = keyframes`
  from {
    transform: rotate(0deg);
  }

  to {
    transform: rotate(360deg);
  }
`;

// Here we create a component that will rotate everything we pass in over two seconds
const Rotate = styled.div`
  display: inline-block;
  animation: ${rotate} 2s linear infinite;
  padding: 2rem 1rem;
  font-size: 1.2rem;
`;

render(<Rotate>&lt; 💅🏾 &gt;</Rotate>);
```

## Tổng kết

1. sử dụng styled-components dạng CSS in ts, ngoài ra cấu trúc có thể viết như SCSS
2. chú ý cách dùng theme, props, css,.attrs, components
3. cách dùng createGlobalStyle,Tagged Template Literals,Animations
