---
layout  : wiki
title   : tableau trusted ticket
summary : 
date    : 2021-10-05 10:56:05 +0900
updated : 2021-10-05 11:27:47 +0900
tags    : tableau trusted ticket
toc     : true
public  : true
parent  : [[/etc/index]]
latex   : false
---
* TOC
{:toc}

# Tableau Trust Ticket 발급받기

## 신뢰할 수 있는 ip 추가

ticket 발급을 위해선 태블로 서버의 접근 허용 ip 목록에 태블로 서버를 내장할 서버 ip가 등록되어있어야 한다.
우선적으로 ticket 발급 test를 위해 본인이 사용중인 pc의 ip를 신뢰할 수 있는 ip로 등록하도록 한다. 

신뢰할 수 있는 ip 등록은 **tsm -> 구성 -> 사용자 ID 및 엑세스 -> 신뢰할 수 있는 인증** 에서 할 수 있다.

## ticket test를 위한 html samle

아래의 코드를 로컬 pc에 생성 후 username, client ip, server ip를 변경한 후에 정상적으로 티켓 발급이 이루어지는지 확인한다. 

```
<html>
<head>
<title>Trusted Ticket Requester</title>
<script type="text/javascript">
  function submitForm(){
    document.getElementById('form1').action =
    document.getElementById('server').value + "/trusted";
  }
</script>
<style type="text/css">
  .style1 {width: 100%;}
  .style2 {width: 429px;}
  #server {width: 254px;}
</style>
</head>
<body>
<h3>Trusted Ticketer</h3>
<form method="POST" id="form1" onSubmit="submitForm()">
  <table class="style1">
    <tr>
      <td class="style2">Username</td>
      <td><input type="text" name="username" value="" /></td>
    </tr>
    <tr>
      <td class="style2">Server</td>
      <td><input type="text" id="server" name="server" value="https://" /></td>
    </tr>
    <tr>
      <td class="style2">Client IP (optional)</td>
      <td><input type="text" id="client_ip" name="client_ip" value="" /></td>
    </tr>
    <tr>
      <td class="style2">Site (leave blank for Default site; otherwise enter the site name)</td>
      <td><input type="text" id="target_site" name="target_site" value="" /></td>
    </tr>
    <tr>
      <td class="style2"><input type="submit" name="submittable" value="Get Ticket" /></td>
      <td>&#160;</td>
    </tr>
  </table>
</form>
<h4>Be sure to add your IP as a Trusted IP address to the server</h4>
</body>
</html>
```


## 로그 level 변경

정상적인 티켓 발급이 이루어지지 않을 경우 원인 파악을 위한 로그 확인이 필요한다.
기본 로그 level을 info(기본)에서 debug로 변경시킨다.
```
tsm configuration set -k vizqlserver.trustedticket.log_level -v debug
tsm pending-changes apply
```

변경 후 정상적용을 위해 **서버 재부팅** 이 필요하다.

### 로그 경로
```
ProgramData\Tableau\Tableau Server\data\tabsvc\logs\vizqlserver\vizql-*.log
```

>  [https://help.tableau.com/current/server/ko-kr/trusted_auth.htm](https://help.tableau.com/current/server/ko-kr/trusted_auth.htm)
