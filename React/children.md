children이란?
===========

컴포넌트를 불러올때, 열린태그와 닫힌태그 사이에 있는 무엇이든 보여줄때 사용된다.



```
const Grid = (props) => {
    const {is_flex, width, padding, margin, bgColor, children} = props;

    return(
        <React.Fragment>
            {children}
        </React.Fragment>
    )
};

Grid.defaultProps=`
    children: null,
    is_flex: false,
    width: "100%",
    padding: false,
    margin: false,
    bg: false,
`;
```

여기서 GridBox는 바깥은 싸는 속성임.
안에 들어오는 것은 children 속성을 사용해야함!

--------------------------------------------

**코드 해석**

```
import React from "react";
import styled from "styled-component";

const Grid = (props) => {
    const {is_flex, width, padding, margin, bg, children} = props;

    const styles = {
        is_flex : is_flex,
        width: width,
        margin: margin,
        padding: padding,
        bg: bg,
    };

    return(
        <React.Fragment>
            {...styles}{children}
        </React.Fragment>
    )
};

Grid.defaultProps=`
    children: null,
    is_flex: false,
    width: "100%",
    padding: false,
    margin: false,
    bg: false,

`;

const GridBox = styled.div`
    width:${(props) => props.width};
    height: 100%;
    box-sizing: border-box; //선굵기까지 포함함
    ${(props) => (props.padding? `padding: ${props.padding}`:"")}
    ${(props) => (props.margin? `margin: ${props.margin}`: "")}
    ${(props) => (props.bg? `bg: ${props.bg}`: "")}
    ${(props) => props.is_flex ? `display:flex; align-items:center; justify-content: space-between;` :""}
`;

export default Grid;
```

원래라면
```
return(
        <React.Fragment>
            {...props}{children}
        </React.Fragment>
    )
```

를 사용하겠지만 {...styled}{children}을 사용한 이유는 children이 style 속성이 아니기 때문에 분리해준다.

따로 styles를 정의해서 나머지 값들을 정의해준다.
