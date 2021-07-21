**delete redux**

```
const DELETE_REVIEW = "review/DELETE_REVIEW";

const deleteReview = createAction(DELETE_REVIEW, (review) => ({review}));

//orderId가져와보기! payload._id
const deleteReviewDB = (reviewId) => {
  console.log(reviewId);
  return function (dispatch, getState, {history}){
    instance
    .delete(`/api/review/${reviewId}`)
    .then((res) => {
      console.log(res);
      dispatch(deleteReview(reviewId));
      window.alert("리뷰가 삭제되었습니다.");
    })
    .catch((err) => {
      window.alert("리뷰 삭제에 오류가 있어요! 관리자에게 문의 부탁드립니다.");
      console.log("err");
    });
  };
};

export default handleActions({
    [DELETE_REVIEW]: (state,action) => produce(state, (draft) => {
      
      console.log(action.payload.review); //지우고픈 리뷰의 아이디가 콘솔에 뜬다.
      
      let idx = draft.list.findIndex((r) => 
      r._id === action.payload.review);
      draft.list.splice(idx, 1); 
      
      //리듀서에서 리덕스에 남아있는 인덱스값 지우기, splice 사용!
      // 조건에 만족하는 idx를 갖고있는 1개를 지워라
      // findIndex로 원하는 값의 위치를 찾을 수 있다.
    })
}, initialState);


export const actionCreators = {
    addReview,
    addReviewDB,
    getReview,
    getReviewDB,
    deleteReview,
    deleteReviewDB,
};
```
**삭제 버튼 있는 페이지**

```
const ReviewItem = (props) => {
  const dispatch = useDispatch();
  // 나중에 데이터에 따라 변경해도 무방!
  const { user_name, star, content, menu, _id } = props;
  const nickname = useSelector((state) => state.user.user_info);
  const menuId = props.menuIdList;
  
  //삭제 버튼
  const deleteBtn = () => {
    dispatch(reviewActions.deleteReviewDB(_id))
  }
  
  return (
    <React.Fragment>
      <Text _onClick = {() => {deleteBtn()}} width="20%">
    </React.Fragment>
    );
    
 export default ReviewItem;
 ```
 
 리덕스 사용할때 해야하는 행동
 =====================
 
 리덕스 만들고 뷰에 dispatch해서 액션을 불러온다.
 
 해당 아이디에 맞는 리뷰를 삭제해야한다.
 
 어떻게 ReviewItem.js에서 deleteReviewDB에 필요한 reviewId를 넘겨줄 수 있을까 ?
 
 또 순서가 여러 개인 경우, 배열의 순서를 어떻게 고려해야하는지 몰라서 계속 헤매고 있었다.
 
 ```
 const { user_name, star, content, menu, _id } = props;
 ```
 이렇게 가져오면 props 요소를 받아올 수 있다.
 
 ```
 const deleteBtn = () => {
    dispatch(reviewActions.deleteReviewDB(_id))
  }
 ```
 버튼 누르면 _id를 deleteReviewDB에 넣어줘서 액션 실행함.
 
 ```
  const _review_list = useSelector((state) => state.review.list);
  console.log(_review_list);
  const index = _review_list.findIndex((r) => r._id == )
 ```
 이렇게 하나하나 따라가지 않고, findIndex로 찾기!
 
 
 
