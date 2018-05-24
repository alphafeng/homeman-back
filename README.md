# homeman-back
homeman后台程序

## account:账户管理
    openid avatarurl nickname
    wxlogin:微信登录

## session:session管理（redis）
    sessionid openid
    getSession
    putSession

## rating:考核管理
    year* week* openid* subjectid score

## rate_subject
    id, name, maxscore

## schedule:日程管理

## finance:财务管理