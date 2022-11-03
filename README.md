<div align="center">
  <img src="./assets/header.png" alt="substats" />
  <h3><a href="https://api.swo.moe/stats">substats</a></h3>
  <p><a href="#get-started">Get started</a> · <a href="#whats-new">What's new?</a> · <a href="#sponsoring">Sponsoring</a></p>
  <p>( ｀д′) <em>how many followers do i have? how many!</em></p>

  <img src="https://img.shields.io/badge/Cloudflare-F69652?style=flat&logo=cloudflare&logoColor=white" alt="Cloudflare Workers" />
  <img src="https://img.shields.io/badge/Version-2.0*-F69652?style=flat&labelColor=2B3137" alt="Version 2.0/substats" />
  <a href="https://github.com/spencerwooo/substats/actions?query=workflow%3ADeploy"><img src="https://github.com/spencerwooo/substats/workflows/Deploy/badge.svg" alt="Vercel" /></a>
</div>

## Get started

> sub · stats /səb ˈ stats/
>
> - a serverless api for getting the number of followers of you in your favourite services

_*Version 2.0 is still in `beta`, not all features are ported from 1.0. Check below for details 👇_

### Basic

```
https://api.swo.moe
```

You request:

```http
GET /stats/:source/:key
```

I respond:

```typescript
{
  source: string,
  key: string,
  failed: true | false,
  count: number | string  // Most often it's a number when source !== 'common'
}
```

Yep, it's that simple now. ;)

_*Note that `key` needs to be url encoded, remember this if you are requesting the `feedly`, `inoreader`, or `feedspub` routes._

### Building badges 🎫

Of course! And as a matter of fact, substats works quite well with [`shields.io`](https://shields.io)'s `/dynamic` route. All these badges below are dynamically generated with substat's data:

[![GitHub](https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fapi.swo.moe%2Fstats%2Fgithub%2Fspencerwooo&query=count&color=181717&label=GitHub&labelColor=282c34&logo=github&suffix=+follows&cacheSeconds=3600)](https://github.com/spencerwooo)
[![Telegram](https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fapi.swo.moe%2Fstats%2Ftelegram%2FrealSpencerWoo&query=count&color=2CA5E0&label=Telegram&labelColor=282c34&logo=telegram&suffix=+members&cacheSeconds=3600)](https://t.me/realSpencerWoo)
[![微博](https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fapi.swo.moe%2Fstats%2Fweibo%2F6265807914&query=count&color=040000&label=%E5%BE%AE%E5%8D%9A&labelColor=e71f19&logo=sina-weibo&suffix=+%E5%85%B3%E6%B3%A8&cacheSeconds=3600)](https://weibo.com/6265807914)
[![少数派](https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fapi.swo.moe%2Fstats%2Fsspai%2Fspencerwoo&query=count&color=d71a1b&label=%E5%B0%91%E6%95%B0%E6%B4%BE&labelColor=282c34&suffix=+%E5%85%B3%E6%B3%A8&cacheSeconds=3600)](https://sspai.com/u/spencerwoo)
[![爱发电](https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fapi.swo.moe%2Fstats%2Fafdian%2Fspencerwoo&query=count&color=282c34&label=%E7%88%B1%E5%8F%91%E7%94%B5&labelColor=946ce6&suffix=+%E5%8F%91%E7%94%B5%E4%BA%BA%E6%AC%A1+%2F+%E6%9C%88&cacheSeconds=3600)](https://afdian.net/@spencerwoo)
[![即刻](https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fapi.swo.moe%2Fstats%2Fjike%2F4DDA0425-FB41-4188-89E4-952CA15E3C5E&query=count&color=fbae00&label=%E5%8D%B3%E5%88%BB&labelColor=282c34&suffix=+%E5%85%B3%E6%B3%A8&cacheSeconds=3600)](https://m.okjike.com/users/4DDA0425-FB41-4188-89E4-952CA15E3C5E)
[![Steam](https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fapi.swo.moe%2Fstats%2Fsteamgames%2F76561198336249957&query=count&color=0b1a37&label=Steam&labelColor=134375&logo=steam&suffix=+games&cacheSeconds=3600)](https://steamcommunity.com/profiles/76561198336249957)
[![知乎](https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fapi.swo.moe%2Fstats%2Fzhihu%2Fbi-xiao-tian-99&query=count&color=282c34&label=%E7%9F%A5%E4%B9%8E&labelColor=0084ff&logo=zhihu&logoColor=ffffff&suffix=+%E5%85%B3%E6%B3%A8&cacheSeconds=3600)](https://www.zhihu.com/people/bi-xiao-tian-99)
[![哔哩哔哩](https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fapi.swo.moe%2Fstats%2Fbilibili%2F401742377&query=count&color=282c34&label=%E5%93%94%E5%93%A9%E5%93%94%E5%93%A9&labelColor=FE7398&logo=data%3Aimage%2Fpng%3Bbase64%2CiVBORw0KGgoAAAANSUhEUgAAAGAAAABgCAYAAADimHc4AAAD7ElEQVR4nO2dW9WrMBCFK6ESkFAJSKiESqgEHCABCZWAhEpAAhL2ecik5dDc%2FpXLBDLfWnlqy0xmJ5BMQnq5CIIgCIIgCIIgCIIgCEIBAHQAemYfrgCunD6wAKAHsEKxALgx+bCQD8%2FS9tmgVqeDr1lLigDgZvDhXso+K9TyTBQRwRJ8AHjntl0Flh5QRAQK%2FmKxPeayWx2OXpBNBKiHvi34b7T2MC4pAvW6twR%2FRwkRKPizBN8CgEcuESj4Lwm+BwBjahEk+H8EwJRKhOaCDzW8e1JLfkUUH1NgmR3XmHffHR1l+72BSs8d7w8U+JDAnZERQMcV+CtUi7dNqFqibB4J7vtrq7xKCuAasbTMXCL4T+5aVk6+2xHUrWdhruAR6HIJcOeu2UHI8zyAe2ytWfEdWz9PVvQ8YAmIQ5dDAB9LFsMVAv8oMO2zAGrC5WNIarRiAuKR9jYEd9pY08aa6uUzIHGRdkgKd8pY0yc1WjEBAqypDYoAG0QAZkQAZkQAZkQAZk4vANQenjsSzS3I%2FwcSbXU5jQBUkRtdf4Rar90v8kSv3+I3ffCCSpk8I%2Fw+lgDkdI%2Fv2rEp2CaiWm1AsDQLlDAD+dlFXLMeAaCSeLZdaSFE5VUQNot38cKuEeBgAsSuG0flVZBmEanbXfNQAsS0fgBYIn2fIu3%2FBBMHEyBmDXlFfA8IzeHb+Ems4WAChKykrVA9ZfsQTL57jXzRg4A5wC%2FA8N4ADiZAZwm2XjW75Qh2KOTfA0p4kygPw28OJcCVgn3nDnYo2EwEYRgGH0qAMyICMCMCMCMCMCMCMCMCMCMCfP3qwHDOQ4AAUekTk8FaBRihJnZdYbvtCGC7LvmkM63GjVDINPFrQgCq5ETXfmMzI90FXzPvfqt7x4rEu%2FZaEcCUxFvgz2zO+BUn6UkoaEEAsptiMSX5e8FoRYCN7cVgb4Vq7U%2FH50Pq4JNP7Qiw8UFnJwcK+tXy+Wj6PLEvPgHSHv5UgwA1IQIwwyFAyLJin9RoxYgAzAQIkPwNmf26busC+OIx5TDqo5nDT+F%2FSS%2F9CYzwb+No49zNy2evkYv0LywGGAXUvp6eSneycqOic0w20k7CNgKE7jJunSGLACTCxF27ylmQc98T5MQUH49swd+I0HPXslLKnT0N+wnkrTKi9JZL%2FL9i1SorMmdeQ4TQQ7OFMxIMzGD45w8nUL1im7efENZLJpgPSw0pfz0cdt4U3230Td%2FTvx2R6d2FrHhEWLkq5PELOMsRPHCPnAZGv1xJteL7jbJiaW3sB2nDvPC%2FosSYvjRQz4cJ6n7KO3rYQL7M+L6nVtfDVRAEQRAEQRAEQRAEIZ5%2FSAXmdfXaoQsAAAAASUVORK5CYII%3D&suffix=+%E5%85%B3%E6%B3%A8&cacheSeconds=3600)](https://space.bilibili.com/401742377)
[![掘金](https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fapi.swo.moe%2Fstats%2Fjuejin%2F1838039172387262&query=count&color=282c34&label=%E6%8E%98%E9%87%91&labelColor=1e80ff&logo=data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMzYiIGhlaWdodD0iMjgiIHZpZXdCb3g9IjAgMCAzNiAyOCIgZmlsbD0ibm9uZSIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KPHBhdGggZmlsbC1ydWxlPSJldmVub2RkIiBjbGlwLXJ1bGU9ImV2ZW5vZGQiIGQ9Ik0xNy41ODc1IDYuNzcyNjhMMjEuODIzMiAzLjQwNTA1TDE3LjU4NzUgMC4wMDc0ODIzN0wxNy41ODM3IDBMMTMuMzU1NSAzLjM5NzU3TDE3LjU4MzcgNi43Njg5NEwxNy41ODc1IDYuNzcyNjhaTTE3LjU4NjMgMTcuMzk1NUgxNy41OUwyOC41MTYxIDguNzc0MzJMMjUuNTUyNiA2LjM5NDUzTDE3LjU5IDEyLjY4MDhIMTcuNTg2M0wxNy41ODI1IDEyLjY4NDVMOS42MTk5MyA2LjQwMjAxTDYuNjYwMTYgOC43ODE4MUwxNy41ODI1IDE3LjM5OTJMMTcuNTg2MyAxNy4zOTU1Wk0xNy41ODI4IDIzLjI4OTFMMTcuNTg2NSAyMy4yODU0TDMyLjIxMzMgMTEuNzQ1NkwzNS4xNzY4IDE0LjEyNTRMMjguNTIzOCAxOS4zNzUyTDE3LjU4NjUgMjhMMC4yODQzNzYgMTQuMzU3NEwwIDE0LjEyOTFMMi45NTk3NyAxMS43NTMxTDE3LjU4MjggMjMuMjg5MVoiIGZpbGw9IiMxRTgwRkYiLz4KPC9zdmc+Cg==&logoColor=ffffff&suffix=+%E5%85%B3%E6%B3%A8&cacheSeconds=3600)](https://juejin.cn/user/1838039172387262)
[![语雀](https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fapi.swo.moe%2Fstats%2Fyuque%2F85213&query=count&color=2CA5E0&label=%E8%AF%AD%E9%9B%80&labelColor=36d07c&logo=data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iVVRGLTgiPz4KPHN2ZyB3aWR0aD0iMTc2cHgiIGhlaWdodD0iMTcycHgiIHZpZXdCb3g9IjAgMCAxNzYgMTcyIiB2ZXJzaW9uPSIxLjEiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyIgeG1sbnM6eGxpbms9Imh0dHA6Ly93d3cudzMub3JnLzE5OTkveGxpbmsiPgogICAgPHRpdGxlPue8lue7hCAy5aSH5Lu9IDI8L3RpdGxlPgogICAgPGRlZnM+CiAgICAgICAgPHJhZGlhbEdyYWRpZW50IGN4PSIzOC4xNzQ3MjEzJSIgY3k9Ijg2LjA3NzY2MDElIiBmeD0iMzguMTc0NzIxMyUiIGZ5PSI4Ni4wNzc2NjAxJSIgcj0iOTcuMDY3Mzc5JSIgZ3JhZGllbnRUcmFuc2Zvcm09InRyYW5zbGF0ZSgwLjM4MTc0NywwLjg2MDc3Nyksc2NhbGUoMC44NTUzNjUsMS4wMDAwMDApLHJvdGF0ZSgtNDYuMzAwNTEyKSx0cmFuc2xhdGUoLTAuMzgxNzQ3LC0wLjg2MDc3NykiIGlkPSJyYWRpYWxHcmFkaWVudC0xIj4KICAgICAgICAgICAgPHN0b3Agc3RvcC1jb2xvcj0iIzE3OEY2NyIgb2Zmc2V0PSIwJSI+PC9zdG9wPgogICAgICAgICAgICA8c3RvcCBzdG9wLWNvbG9yPSIjMzFDQzc5IiBzdG9wLW9wYWNpdHk9IjAuNTUiIG9mZnNldD0iNTQuNjg0NzY4NCUiPjwvc3RvcD4KICAgICAgICAgICAgPHN0b3Agc3RvcC1jb2xvcj0iIzUzRTY4RCIgc3RvcC1vcGFjaXR5PSIwLjgiIG9mZnNldD0iMTAwJSI+PC9zdG9wPgogICAgICAgIDwvcmFkaWFsR3JhZGllbnQ+CiAgICAgICAgPHBhdGggZD0iTTc2LjU2Njk3MzQsNy4xMDU0MjczNmUtMTUgTDc3LjEzMjI0ODUsNy4xMDU0MjczNmUtMTUgTDc3LjYzMTcxMzMsNy4xMDU0MjczNmUtMTUgTDc3LjYzMTcxMzMsNy4xMDU0MjczNmUtMTUgTDc4LjE0MDg3NzEsMC4wMDI1ODQ4ODQyNyBMNzguMTQwODc3MSwwLjAwMjU4NDg4NDI3IEw3OC42NTk2NTc0LDAuMDA1MzE2NTM5MjUgTDc4LjY1OTY1NzQsMC4wMDUzMTY1MzkyNSBMNzkuMTg3OTcxNywwLjAwOTA2MjU4ODkxIEw3OS4xODc5NzE3LDAuMDA5MDYyNTg4OTEgTDc5LjcyNTczNzQsMC4wMTM4NjQyMjI4IEw3OS43MjU3Mzc0LDAuMDEzODY0MjIyOCBMODAuMjcyODcyMywwLjAxOTc2MjYzMDYgTDgwLjI3Mjg3MjMsMC4wMTk3NjI2MzA2IEw4MC44MjkyOTM3LDAuMDI2Nzk5MDAxOCBMODAuODI5MjkzNywwLjAyNjc5OTAwMTggTDgxLjIwNTM1OTgsMC4wMzIxNDI0NTg0IEw4MS4yMDUzNTk4LDAuMDMyMTQyNDU4NCBMODEuNTg1NDkyMSwwLjAzODAyMjE4NzIgTDgxLjU4NTQ5MjEsMC4wMzgwMjIxODcyIEw4Mi4xNjMyNjE1LDAuMDQ3ODczOTg4MSBMODIuMTYzMjYxNSwwLjA0Nzg3Mzk4ODEgTDgyLjc1MDA0MjYsMC4wNTkwMDEwNTExIEw4Mi43NTAwNDI2LDAuMDU5MDAxMDUxMSBMODMuMzQ1NzUyOSwwLjA3MTQ0NDU2NTYgTDgzLjM0NTc1MjksMC4wNzE0NDQ1NjU2IEw4My43NDc4MTMxLDAuMDgwNDkxOTQ0NSBMODMuNzQ3ODEzMSwwLjA4MDQ5MTk0NDUgTDg0LjM1ODIyMjEsMC4wOTUyMjEwNzc1IEw4NC4zNTgyMjIxLDAuMDk1MjIxMDc3NSBMODQuOTc3MzQwNSwwLjExMTM3NjUwMSBMODQuOTc3MzQwNSwwLjExMTM3NjUwMSBMODUuNjA1MDg1NywwLjEyODk5OTQwNSBMODUuNjA1MDg1NywwLjEyODk5OTQwNSBMODYuMDI4MzM0NCwwLjE0MTU4MzYxNCBMODYuMDI4MzM0NCwwLjE0MTU4MzYxNCBMODYuNjcwMjc0NCwwLjE2MTc0Mzg1IEw4Ni42NzAyNzQ0LDAuMTYxNzQzODUgTDg3LjMyMDYyMTMsMC4xODM0ODE0MDYgTDg3LjMyMDYyMTMsMC4xODM0ODE0MDYgTDg3Ljc1ODgxNTcsMC4xOTg4Njk3MzggTDg3Ljc1ODgxNTcsMC4xOTg4Njk3MzggTDg4LjIwMDY4NTQsMC4yMTQ5ODk2MTEgTDg4LjIwMDY4NTQsMC4yMTQ5ODk2MTEgTDg4LjY0NjIwNiwwLjIzMTg1MzIzMSBMODguNjQ2MjA2LDAuMjMxODUzMjMxIEw4OS4wOTUzNTMsMC4yNDk0NzI4MDEgTDg5LjA5NTM1MywwLjI0OTQ3MjgwMSBMODkuNTQ4MTAyMSwwLjI2Nzg2MDUyNSBMODkuNTQ4MTAyMSwwLjI2Nzg2MDUyNSBMOTAuMDA0NDI4NywwLjI4NzAyODYwNyBMOTAuMDA0NDI4NywwLjI4NzAyODYwNyBMOTAuNjk1NTczMSwwLjMxNzI3MDYwMSBMOTAuNjk1NTczMSwwLjMxNzI3MDYwMSBMOTEuMTYwNzM2OCwwLjMzODQ0Mjk3NSBMOTEuMTYwNzM2OCwwLjMzODQ0Mjk3NSBMOTEuODY1MDIyMywwLjM3MTc0ODYxMiBMOTEuODY1MDIyMywwLjM3MTc0ODYxMiBMOTIuMzM4ODcwMiwwLjM5NTAwMTU1NCBMOTIuMzM4ODcwMiwwLjM5NTAwMTU1NCBMOTIuODE2MTQ5MiwwLjQxOTEwODA3OSBMOTIuODE2MTQ5MiwwLjQxOTEwODA3OSBMOTMuNTM4NDQ3MiwwLjQ1Njg5NTAzNyBMOTMuNTM4NDQ3MiwwLjQ1Njg5NTAzNyBMOTQuMDI0MTk2NywwLjQ4MzE4ODkxOCBMOTQuMDI0MTk2NywwLjQ4MzE4ODkxOCBMOTQuNTEzMjkxNiwwLjUxMDM3OTA5OSBMOTQuNTEzMjkxNiwwLjUxMDM3OTA5OSBMOTUuMDA1NzA3NSwwLjUzODQ3Nzc4NSBMOTUuMDA1NzA3NSwwLjUzODQ3Nzc4NSBMOTUuNTAxNDIsMC41Njc0OTcxNzkgTDk1LjUwMTQyLDAuNTY3NDk3MTc5IEw5Ni4wMDA0MDQ2LDAuNTk3NDQ5NDg1IEw5Ni4wMDA0MDQ2LDAuNTk3NDQ5NDg1IEw5Ni41MDI2MzY5LDAuNjI4MzQ2OTA5IEw5Ni41MDI2MzY5LDAuNjI4MzQ2OTA5IEw5Ny4wMDgwOTI1LDAuNjYwMjAxNjU0IEw5Ny4wMDgwOTI1LDAuNjYwMjAxNjU0IEw5Ny41MTY3NDY5LDAuNjkzMDI1OTI1IEw5Ny41MTY3NDY5LDAuNjkzMDI1OTI1IEw5OC4wMjg1NzU3LDAuNzI2ODMxOTI2IEw5OC4wMjg1NzU3LDAuNzI2ODMxOTI2IEw5OC41NDM1NTQ1LDAuNzYxNjMxODYxIEw5OC41NDM1NTQ1LDAuNzYxNjMxODYxIEMxMTcuMDM0Mzk4LDIuMDI1MzA0OCAxMjEuOTMxNTEzLDE1LjM0MTQ3NTIgMTIyLjQ1MjYsMTYuOTM0ODY2NCBMMTIyLjQ4MDAwNywxNy4wMjA0MjI4IEwxMjIuNDgwMDA3LDE3LjAyMDQyMjggTDEyMi41MDEyOTMsMTcuMDkwNTE2NiBMMTIyLjUwMTI5MywxNy4wOTA1MTY2IEwxMzAuNTI4NDYzLDE3LjUyNzU5NyBMMTMwLjUyODQ2MywxNy41Mjc1OTcgQzEzMC45NTY4MjksMTcuNTI3NTk3IDEzMS4zMDQwODgsMTcuODc0ODU2MyAxMzEuMzA0MDg4LDE4LjMwMzIyMjMgQzEzMS4zMDQwODgsMTguNjEwMjUxNSAxMzEuMTI1NjkzLDE4Ljg3NTYxNDMgMTMwLjg2NjkwMiwxOS4wMDEzMTEgQzEyMi42MjcyODUsMjMuNDU5ODY0IDEyMC4xMTAwNTQsMzIuNTE5NDQ1MSAxMjEuNTg5OTU2LDM4LjQyMDc2NjggQzEyMi4wNjY5MTMsNDAuMzIyNzAxNiAxMjIuODA3OTUxLDQxLjk1NzYzODUgMTIzLjYzMjkyOCw0My42ODU3MTQ0IEwxMjQuMTU0MTY2LDQ0Ljc3MzQ2MzUgQzEyNi4wNjM4Miw0OC43Njc2NzM2IDEyOC4yMDc5MjUsNTMuNjA0MTIwOCAxMjguNTU4MDU0LDYzLjMzODAxODQgQzEyOS4zNDE4MTEsODUuMTI3MjE1NCAxMTAuMTg4Nzc1LDEwNC43MTA2NjkgODcuNTI1NjcwOSwxMDQuNzEwNjY5IEw4Ny4yNzc2NzczLDEwNC43MTA3NjggTDg3LjI3NzY3NzMsMTA0LjcxMDc2OCBMODYuNzQ4MzYwMiwxMDQuNzExNTU5IEw4Ni43NDgzNjAyLDEwNC43MTE1NTkgTDg1Ljg3MTA1OTgsMTA0LjcxNDIyOCBMODUuODcxMDU5OCwxMDQuNzE0MjI4IEw4NS4yMzA2NDI5LDEwNC43MTY5OTYgTDg1LjIzMDY0MjksMTA0LjcxNjk5NiBMODQuMTg2NjkyOCwxMDQuNzIyNjMxIEw4NC4xODY2OTI4LDEwNC43MjI2MzEgTDgzLjQzNTE3NjEsMTA0LjcyNzM3NyBMODMuNDM1MTc2MSwxMDQuNzI3Mzc3IEw4Mi42MzkyMTk2LDEwNC43MzI5MTMgTDgyLjYzOTIxOTYsMTA0LjczMjkxMyBMODEuMzYxOTU5OSwxMDQuNzQyNzAxIEw4MS4zNjE5NTk5LDEwNC43NDI3MDEgTDc5Ljk4NDcxMDUsMTA0Ljc1NDI2OCBMNzkuOTg0NzEwNSwxMDQuNzU0MjY4IEw3OC41MDc0NzEzLDEwNC43Njc2MTQgTDc4LjUwNzQ3MTMsMTA0Ljc2NzYxNCBMNzYuMzgyMjc5MywxMDQuNzg4MTc4IEw3Ni4zODIyNzkzLDEwNC43ODgxNzggTDc0LjY3MTczMDYsMTA0LjgwNTY3NyBMNzQuNjcxNzMwNiwxMDQuODA1Njc3IEw3MS41OTg2MTY1LDEwNC44Mzg3OTYgTDcxLjU5ODYxNjUsMTA0LjgzODc5NiBMNjguMjQ3NzUzLDEwNC44NzY4NTggTDY4LjI0Nzc1MywxMDQuODc2ODU4IEw2NC42MTkxNDAxLDEwNC45MTk4NjQgTDY0LjYxOTE0MDEsMTA0LjkxOTg2NCBMNjIuMzA4NjUyNywxMDQuOTQ4MDQgTDYyLjMwODY1MjcsMTA0Ljk0ODA0IEw1OS4wNzI0NjMsMTA0Ljk4ODM3NiBMNTkuMDcyNDYzLDEwNC45ODgzNzYgTDU0Ljc3NzI1MTUsMTA1LjA0MzI0NSBMNTQuNzc3MjUxNSwxMDUuMDQzMjQ1IEw1MC4yMDQyOTA2LDEwNS4xMDMwNTggTDUwLjIwNDI5MDYsMTA1LjEwMzA1OCBMNDYuMzQ1OTQyMywxMDUuMTU0NDY3IEw0Ni4zNDU5NDIzLDEwNS4xNTQ0NjcgTDQwLjIyNTEyMDUsMTA1LjIzNzUxMiBMNDAuMjI1MTIwNSwxMDUuMjM3NTEyIEwzNS45MjIzNzMyLDEwNS4yOTY4MyBMMzUuOTIyMzczMiwxMDUuMjk2ODMgTDI3Ljk2NDgzMTIsMTA1LjQwODI0OSBMMjcuOTY0ODMxMiwxMDUuNDA4MjQ5IEwxOS40NjI5MDAzLDEwNS41MjkzNTcgTDE5LjQ2MjkwMDMsMTA1LjUyOTM1NyBMMTEuNzQyMjQxOSwxMDUuNjQwODc1IEwxMS43NDIyNDE5LDEwNS42NDA4NzUgTDcuNzMxOTI4MDUsMTA1LjY5OTMwMyBMNTYuMTk2NDM3Nyw1MC41ODcxMDMxIEw1Ni42MzU2MjgsNTAuMDg2NDg2NyBMNTYuNjM1NjI4LDUwLjA4NjQ4NjcgTDU3LjA3MzYyNjcsNDkuNTg4MzQ2MSBMNTcuMDczNjI2Nyw0OS41ODgzNDYxIEw1Ny41MTAzMzQ0LDQ5LjA5MjU1MDggTDU3LjUxMDMzNDQsNDkuMDkyNTUwOCBMNTkuNjcxMDIyOSw0Ni42NDQxOTUgTDU5LjY3MTAyMjksNDYuNjQ0MTk1IEw2MC4wOTc4OTM3LDQ2LjE1OTczNTYgTDYwLjA5Nzg5MzcsNDYuMTU5NzM1NiBMNjAuNTIyNzc2Niw0NS42NzY3MDk0IEw2MC41MjI3NzY2LDQ1LjY3NjcwOTQgTDYwLjk0NTU3MTksNDUuMTk0OTg2MiBDNjEuMDE1ODU4Myw0NS4xMTQ4MDAzIDYxLjA4NjA1MzYsNDUuMDM0NjYzMiA2MS4xNTYxNTU3LDQ0Ljk1NDU3MjQgTDYxLjU3NTYzMzIsNDQuNDc0NTU5IEM2MS42NDUzNTQyLDQ0LjM5NDY0MTggNjEuNzE0OTc3OCw0NC4zMTQ3NjU0IDYxLjc4NDUwMiw0NC4yMzQ5MjY5IEw2Mi4yMDA0Mzc2LDQzLjc1NjMzMDMgTDYyLjIwMDQzNzYsNDMuNzU2MzMwMyBMNjIuNjEzODg3NSw0My4yNzg1MTUzIEM2Ny40MjI1ODI0LDM3LjcwODA1OTUgNzEuNzAzNDUzMSwzMi4yNzA1NzE5IDc0Ljc0NTA5MjcsMjYuMDM0ODA4OSBDNzguMTIxNDAyOCwxNi40OTg4MTE3IDc0LjY4NDMxNDEsOS4zODMwNTQ5MiA3MS4xNzU3NjkyLDUuMDcxNTE1ODkgQzcwLjkwNDg3NTMsNC43Mzg2MjMwNSA3MC42MzM1NTU1LDQuNDIyNDQ3MTMgNzAuMzY0OTEyOCw0LjEyMzE2NDg0IEM2OS4xNjg4Njc4LDIuNTkyMTQ0OTIgNjkuOTgzMjIyMSwwLjA0MTM4OTM1OTQgNzIuMjYwODcyNywwLjA0MTM4OTM1OTQgQzcyLjQ0NjQ2MTgsMC4wNDEzODkzNTk0IDcyLjYzNTgyMTcsMC4wMzg1MjEwMjQ3IDcyLjgyODkzNDgsMC4wMzQ4MjA4NTg2IEw3My4yNjk3NjQ5LDAuMDI1OTUwOTE5NSBDNzMuMzY5MTMxMiwwLjAyNDA0OTcyOTUgNzMuNDY5NDMyNCwwLjAyMjMyMjQyNjEgNzMuNTcwNjY2NCwwLjAyMTAyMzU3MjEgTDczLjk5MTIwMjMsMC4wMTU5ODU1MzYzIEw3My45OTEyMDIzLDAuMDE1OTg1NTM2MyBMNzQuNDIyMDY5OSwwLjAxMTU1NjcxNjMgTDc0LjQyMjA2OTksMC4wMTE1NTY3MTYzIEw3NC43MTUwMTQsMC4wMDg5NjI5Mjc1OSBMNzQuNzE1MDE0LDAuMDA4OTYyOTI3NTkgTDc1LjQ2NzE0MzYsMC4wMDM4MjI5NDE2OSBMNzUuNDY3MTQzNiwwLjAwMzgyMjk0MTY5IEw3Ni4wODg5OCwwLjAwMTE5NDM2MDg1IEw3Ni4wODg5OCwwLjAwMTE5NDM2MDg1IEw3Ni41NjY5NzM0LDcuMTA1NDI3MzZlLTE1IEw3Ni41NjY5NzM0LDcuMTA1NDI3MzZlLTE1IFoiIGlkPSJwYXRoLTIiPjwvcGF0aD4KICAgICAgICA8bGluZWFyR3JhZGllbnQgeDE9IjgxLjQ2ODIyNTMlIiB5MT0iNTcuMTg4NDQ2OCUiIHgyPSItOC4yMzU5NTEyMyUiIHkyPSI3OS4xMjM3NjA3JSIgaWQ9ImxpbmVhckdyYWRpZW50LTMiPgogICAgICAgICAgICA8c3RvcCBzdG9wLWNvbG9yPSIjRkZGRkZGIiBzdG9wLW9wYWNpdHk9IjAiIG9mZnNldD0iMCUiPjwvc3RvcD4KICAgICAgICAgICAgPHN0b3Agc3RvcC1jb2xvcj0iI0Q2RjA1NiIgb2Zmc2V0PSIxMDAlIj48L3N0b3A+CiAgICAgICAgPC9saW5lYXJHcmFkaWVudD4KICAgICAgICA8cGF0aCBkPSJNNTYuMTk2NDM3Nyw1MC41ODcxMDMxIEMzNS4yMjA0MDM4LDc0LjE5MjI3MTYgMTAuMjU1NDg1NywxMDIuOTEyNzUzIDAuNzc5MTc4ODg2LDExMy43MDE0MzUgQy0xLjA0NjMxODgsMTE1Ljc3OTc0NyAwLjcyMzAwOTczMSwxMTcuNzQyMjk0IDIuMTM3MDY3MjcsMTE3Ljk4NTM5OCBDNzIuODM2NDEwOCwxMzAuMTQwMDI4IDk1LjI4Mzg5NDYsOTYuODIzMDgwOSAxMDAuMjg0MDc3LDgxLjU5Mjg5MDEgQzEwNy4xMjUyOTYsNjAuNzU1MDM2NSA5Ny40NTkwMDA4LDUwLjU4NzEwMzEgOTEuOTg4NTU2Niw0Ny4yNzEzMTMzIEM3My40Mzg1OTU4LDM2LjAyNzY2MTQgNTkuNjc1MzY2Niw0Ni42NzIxMjU2IDU2LjE5NjQzNzcsNTAuNTg3MTAzMSBaIiBpZD0icGF0aC00Ij48L3BhdGg+CiAgICA8L2RlZnM+CiAgICA8ZyBpZD0i5o6n5Lu2IiBzdHJva2U9Im5vbmUiIHN0cm9rZS13aWR0aD0iMSIgZmlsbD0ibm9uZSIgZmlsbC1ydWxlPSJldmVub2RkIj4KICAgICAgICA8ZyBpZD0ibG9nbyIgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoMTcuOTMzMTU0LCAzMC4xMzUyNzkpIj4KICAgICAgICAgICAgPGcgaWQ9Iui3r+W+hCI+CiAgICAgICAgICAgICAgICA8dXNlIGZpbGw9IiMzMUNDNzkiIHhsaW5rOmhyZWY9IiNwYXRoLTIiPjwvdXNlPgogICAgICAgICAgICAgICAgPHVzZSBmaWxsLW9wYWNpdHk9IjAuNjAwMDAwMDI0IiBmaWxsPSJ1cmwoI3JhZGlhbEdyYWRpZW50LTEpIiB4bGluazpocmVmPSIjcGF0aC0yIj48L3VzZT4KICAgICAgICAgICAgPC9nPgogICAgICAgICAgICA8ZyBpZD0iRmlsbC0xMi1Db3B5Ij4KICAgICAgICAgICAgICAgIDx1c2UgZmlsbD0iIzkzRTY1QyIgeGxpbms6aHJlZj0iI3BhdGgtNCI+PC91c2U+CiAgICAgICAgICAgICAgICA8dXNlIGZpbGwtb3BhY2l0eT0iMC43NSIgZmlsbD0idXJsKCNsaW5lYXJHcmFkaWVudC0zKSIgc3R5bGU9Im1peC1ibGVuZC1tb2RlOiBvdmVybGF5OyIgeGxpbms6aHJlZj0iI3BhdGgtNCI+PC91c2U+CiAgICAgICAgICAgIDwvZz4KICAgICAgICA8L2c+CiAgICA8L2c+Cjwvc3ZnPg==&suffix=+%E5%85%B3%E6%B3%A8&cacheSeconds=3600)](https://www.yuque.com/lyndon)

You can easily create your own badge with our badge builder at [substats.swo.moe](https://substats.swo.moe/).

![Badge builder screenshot](assets/badge-builder-screenshot.png)

### Advanced - the `/common` route 🍀

What if the source you are trying to use is not supported yet, but it's just a simple `GET` request? In this case, you can use the route:

```http
GET /stats/common?endpoint=<url>&datapath=<path>
```

Such as:

```http
GET /stats/common/?endpoint=https://api.genshin.dev/domains/cecilia-garden&datapath=rewards.0.details.2.mora
```

In this case, the `endpoint` is an API url:

```
https://api.genshin.dev/domains/cecilia-garden
```

The response this URL returns looks like:

```jsonc
{
  "name": "Cecilia Garden",
  "type": "Forgery",
  // ...
  "rewards": [
    {
      "details": [
        { /* ... */ },
        { /* ... */ },
        {
          "mora": 1125,
        },
      ]
    }
  ]
}
```

Hence, we provide the `datapath` as `rewards.0.details.2.mora`. (I specifically chose this data as it contains an array to demonstrate how to reference the value `mora` inside the array by index.)

Response from the `endpoint` provided by you is parsed with [object-path](https://github.com/mariocasciaro/object-path), and the method for constructing a reference `datapath` to your value in the response is the same.

Try our `/common` route API URL builder here: [substats.swo.moe/common](https://substats.swo.moe/common).

![Common route screenshot](assets/common-route-screenshot.png)

## Supported sources

- afdian
- bilibili
- coolapk
- feedly
- feedspub
- github
- inoreader
- instagram
- jike
- medium
- neteasemusic
- reddit
- sspai
- steamgames
- steamfriends
- telegram
- twitter
- unsplash
- weibo
- wikipediazh
- zhihu
- juejin
- yuque

<a href="https://api.swo.moe/stats/afdian/afdian"><img src="docs/public/assets/sources/logo_afdian.png" width="auto" height="64px" alt="logo_afdian" /></a>
<a href="https://api.swo.moe/stats/bilibili/401742377"><img src="docs/public/assets/sources/logo_bilibili.png" width="auto" height="64px" alt="logo_bilibili" /></a>
<a href="https://api.swo.moe/stats/coolapk/466253"><img src="docs/public/assets/sources/logo_coolapk.png" width="auto" height="64px" alt="logo_coolapk" /></a>
<a href="https://api.swo.moe/stats/feedly/https%3A%2F%2Fnnw.ranchero.com%2Ffeed.xml"><img src="docs/public/assets/sources/logo_feedly.png" width="auto" height="64px" alt="logo_feedly" /></a>
<a href="https://api.swo.moe/stats/feedspub/https%3A%2F%2Fnnw.ranchero.com%2Ffeed.xml"><img src="docs/public/assets/sources/logo_feedspub.png" width="auto" height="64px" alt="logo_feedspub" /></a>
<a href="https://api.swo.moe/stats/github/spencerwooo"><img src="docs/public/assets/sources/logo_github.png" width="auto" height="64px" alt="logo_github" /></a>
<a href="https://api.swo.moe/stats/inoreader/https%3A%2F%2Fnnw.ranchero.com%2Ffeed.xml"><img src="docs/public/assets/sources/logo_inoreader.png" width="auto" height="64px" alt="logo_inoreader" /></a>
<a href="https://api.swo.moe/stats/instagram/9gag"><img src="docs/public/assets/sources/logo_ins.png" width="auto" height="64px" alt="logo_ins" /></a>
<a href="https://api.swo.moe/stats/jike/2204A477-38C8-4D9D-9705-9C9B990BE042"><img src="docs/public/assets/sources/logo_jike.png" width="auto" height="64px" alt="logo_jike" /></a>
<a href="https://api.swo.moe/stats/medium/SpencerWooo"><img src="docs/public/assets/sources/logo_medium.png" width="auto" height="64px" alt="logo_medium" /></a>
<a href="https://api.swo.moe/stats/neteasemusic/416608258"><img src="docs/public/assets/sources/logo_neteasemusic.png" width="auto" height="64px" alt="logo_neteasemusic" /></a>
<a href="https://api.swo.moe/stats/reddit/jushoro"><img src="docs/public/assets/sources/logo_reddit.png" width="auto" height="64px" alt="logo_reddit" /></a>
<a href="https://api.swo.moe/stats/sspai/spencerwoo"><img src="docs/public/assets/sources/logo_sspai.png" width="auto" height="64px" alt="logo_sspai" /></a>
<a href="https://api.swo.moe/stats/steam/401742377"><img src="docs/public/assets/sources/logo_steam.png" width="auto" height="64px" alt="logo_steam" /></a>
<a href="https://api.swo.moe/stats/telegram/realSpencerWoo"><img src="docs/public/assets/sources/logo_tg.png" width="auto" height="64px" alt="logo_tg" /></a>
<a href="https://api.swo.moe/stats/twitter/GenshinImpact"><img src="docs/public/assets/sources/logo_twitter.png" width="auto" height="64px" alt="logo_twitter" /></a>
<a href="https://api.swo.moe/stats/unsplash/adamhoang"><img src="docs/public/assets/sources/logo_unsplash.png" width="auto" height="64px" alt="logo_unsplash" /></a>
<a href="https://api.swo.moe/stats/weibo/5648729445"><img src="docs/public/assets/sources/logo_weibo.png" width="auto" height="64px" alt="logo_weibo" /></a>
<a href="https://api.swo.moe/stats/wikipediazh/ChenSimon"><img src="docs/public/assets/sources/logo_wikipedia.png" width="auto" height="64px" alt="logo_wikipedia" /></a>
<a href="https://api.swo.moe/stats/zhihu/bi-xiao-tian-99"><img src="docs/public/assets/sources/logo_zhihu.png" width="auto" height="64px" alt="logo_zhihu" /></a>
<a href="https://api.swo.moe/stats/juejin/1838039172387262"><img src="docs/public/assets/sources/logo_juejin.png" width="auto" height="64px" alt="logo_juejin" /></a>
<a href="https://api.swo.moe/stats/yuque/lyndon"><img src="docs/public/assets/sources/logo_yuque.png" width="auto" height="64px" alt="logo_yuque" /></a>

## What's new?

Yes, `substats` is now version `v2.0-beta`! Most of the updates are under-the-hood apart from API formats.

- [x] Refactored in TypeScript.
- [x] Updated to CloudFlare's module workers.
- [x] Worker is built with `esbuild` instead of `webpack`, extra fast!
- [x] Support for Newsblur has been deprecated ~~(seems nobody uses it)~~.
- [x] KV storages are now supported, some routes including `instagram` and `inoreader` depends on this for storing cookies (wip).
- [x] Caching is ported to module workers in 2.0 and supported as always.
- [x] New documentation and query builder.

If you are looking for the multiple source and query functions in 2.0 - it's still under refactor, as `itty-router` does not parse multiple query parameters, blocking this feature here. You can still use the 1.0 route while we wait. [README and documentation for v1.0 (deprecated)](https://github.com/spencerwooo/substats/blob/1becc576f09b09cfa1389312d081f02a25ed0735/README.md).

## Contributing

This is a monorepo managed by `pnpm`. Directory `./worker` holds the Cloudflare Worker module, and `./docs` is a React site for documentation (powered by [Vite](https://vitejs.dev/) and [Chakra UI](https://chakra-ui.com/)). Check the README.md for both packages for details.

## Sponsoring

Open-source is hard! If you happen to like this project and want me to keep going, please consider sponsoring me or providing a single donation! Thanks for all the love and support!

[🧸 Please donate - 微信/支付宝](https://ovi.swo.moe/sponsor) · [Patreon](https://www.patreon.com/spencerwoo) · [爱发电](https://afdian.net/@spencerwoo)

## License

[MIT](LICENSE)

<div align="center">
  <img src="assets/footer.png" />
  <em>made with ❤️ by <a href="https://spencerwoo.com">spencer woo</a></em>
</div>
