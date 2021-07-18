```
const Register = (props) => {
  const dispatch = useDispatch();
  const formik = useFormik({
    initialValues: {
      userId: "",
      pwd: "",
      userName: "",
      phoneNumber: "",
    },

    validationSchema: Yup.object({
      userId: Yup.string()
        .email("이메일을 올바르게 입력해주세요.")
        .required("이메일을 입력하세요."),
      pwd: Yup.string()
        .min(8, "비밀번호는 8자리 이상이어야 합니다.")
        .matches(
          /^(?=.*[A-Za-z])(?=.*\d)[A-Za-z\d]{8,20}$/,
          "영문/숫자 포함 조합 (8~20자)"
        )
        .required("비밀번호를 입력하세요."),
      userName: Yup.string().required("이름을 정확히 입력하세요."),
      phoneNumber: Yup.string().required("휴대폰 번호를 정확하게 입력하세요."),
    }),

    onSubmit: (values) => {
      dispatch(userActions.signUpDB(values))
    },
  });
  ```
  
  stirng()은 문자열을 숫자로 변경하는 함수다.
