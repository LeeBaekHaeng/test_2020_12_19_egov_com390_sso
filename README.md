# test_2020_12_19_egov_com390_sso
SSO 연계 서비스 테스트

목차
1. GodSSOLoginFilter
2. sso 로그인 화면
3. sso 로그인 성공 처리
4. EgovSSOLoginFilter
5. EgovSpringSecurityLoginFilter
6. 브라우저 테스트

---

1. GodSSOLoginFilter
	response.sendRedirect("/sso/loginView.do");

2. sso 로그인 화면
	/sso/loginView.do

3. sso 로그인 성공 처리
	/sso/loginComplete.do

4. EgovSSOLoginFilter

5. EgovSpringSecurityLoginFilter

6. 브라우저 테스트
	http://localhost:8080/sso/uat/uap/selectLoginPolicyList.do
	http://localhost:8080/sso/uat/uia/egovLoginUsr.do

---

2.1 Globals.Auth = security
2.2 EgovSSOLoginFilter 추가
2.3 EgovSSOServiceImpl 추가
2.4 hasTokenInSSOServer return true
2.5 getLoginVO setUniqId setUserSe
2.6 'URL에 세미콜론(semicolon)허용 여부(기본값/false)' 주석 제거
2.7 EgovSSOLoginFilter chain.doFilter(request, response); 후 코드 주석
2.8 springSecurity.setPostOnly(false);
2.9 끝

