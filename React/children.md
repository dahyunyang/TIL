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
