# test_2020_12_19_egov_com390_sso
SSO 연계 서비스 테스트

test_2020_12_19_egov_com390_sso

https://www.egovframe.go.kr/wiki/doku.php?id=egovframework:com:v2:uat:sso%EC%97%B0%EA%B3%84_%EC%84%9C%EB%B9%84%EC%8A%A4

https://github.com/LeeBaekHaeng/test_2020_12_19_egov_com390_sso

1. .gitignore 수정

2. '공통 > 공통' 공통 컴포넌트 설치

3. 'Globals.Auth = security'로 수정
E:\EGOVFRAME390\git\test_2020_12_19_egov_com390_sso\god.sso\src\main\resources\egovframework\egovProps\globals.properties
Globals.Auth = security

http://localhost:8080/sso/uat/uap/selectLoginPolicyList.do
http://localhost:8080/sso/uat/uia/egovLoginUsr.do

4. EgovSSOLoginFilter 추가
/god.sso/src/main/java/egovframework/com/cmm/config/EgovWebApplicationInitializer.java
FilterRegistration.Dynamic egovSSOLoginFilter = servletContext.addFilter("egovSSOLoginFilter", new EgovSSOLoginFilter());
egovSSOLoginFilter.addMappingForUrlPatterns(null, false, "*.do");

No SSO ServiceImpl Class!

egovSSOService

EgovSSOServiceImpl 생성
@Service("egovSSOService")

5. hasTokenInSSOServer 수정
/god.sso/src/main/java/egovframework/com/uat/sso/filter/EgovSSOLoginFilter.java
hasTokenInSSOServer
SSO 통합 인증 서버에 인증여부를 확인 하는 메서드

getLoginVO
토큰 정보를 바탕으로 loginVO 객체를 생성하는 메서드

select EMPLYR_ID, ESNTL_ID, a.* from COMTNEMPLYRINFO a;
업무사용자

HTTP 상태 404 – 찾을 수 없음
/sso/egov_security_login
Origin 서버가 대상 리소스를 위한 현재의 representation을 찾지 못했거나, 그것이 존재하는지를 밝히려 하지 않습니다.

// springSecurity.setRequiresAuthenticationRequestMatcher(new AntPathRequestMatcher(request.getServletContext().getContextPath() +"/egov_security_login", "POST"));
springSecurity.setRequiresAuthenticationRequestMatcher(new AntPathRequestMatcher(request.getServletContext().getContextPath() +"/egov_security_login", "GET"));
springSecurity.setPostOnly(false);

getAttribute: 세션이 이미 무효화되었습니다.

The request was rejected because the URL contained a potentially malicious String ";"

/god.sso/src/main/resources/egovframework/spring/com/context-security.xml
URL에 세미콜론(semicolon)허용 여부(기본값/false) 주석 제거

