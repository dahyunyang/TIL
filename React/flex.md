flex
=====

```
const GridBox = styled.div`
    width:${(props) => props.width};
    height: 100%;
    box-sizing: border-box; //선굵기까지 포함함
    ${(props) => (props.padding? `${props.padding}`:"")}
    ${(props) => (props.margin? `${props.margin}`: "")}
    ${(props) => (props.bg? `${props.bg}`: "")}
    ${(props) => props.is_flex ? `display:flex; align-items:center; justify-content: space-between;` :""}
`;
```

**box-sizing: border-box;**

: 선굵기까지 박스의 크기에 포함한다

**justify-content: space-between;**

: 가로축을 기준으로 좌우에 대한 정렬을 관장함 -  요소들 사이에 동일한 간격을 둔다.

	flex-start (default)	                >>  요소들을 컨테이너의 왼쪽으로 정렬

	flex-end					>>   요소들을 컨테이너의 우측으로 정렬

	center					>> 요소들을 컨테이너의 중앙으로 정렬

	space-between		                >> 요소들 사이에 동일한 간격을 둡니다.

	space-around	        		>> 요소들 주위에 동일한 간격을 둡니다.

	space-evenly(FireFox Only)	        >> 첫번째로 오는 정렬 대상 전에 두개 의 인접한 정렬



출처: https://ipex.tistory.com/entry/CSS3-flex-Box-justifycontent-alignitems [깍돌이]
