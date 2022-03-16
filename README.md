# jwt-exp
Jwt Nedir

Jwt yazılım dünyasında JSON Objelerin transferinde kullanılan güvenlik birimidir.Kendine ait bir algoritma kullanarak oluşturulan token sayesinde uygulamaya erişim engellenip , yetkilendirilebilir.

JWT mimarisi 3 bölümden oluşur.

<h2>Header </h2>

{
   “alg”: “HS256”,
   “typ”: “JWT”
}

* alg : Tokenı imzalamak ve bütünlüğü sağlamak amacı ile kullanılan şifreleme algoritmasıdır.
* typ : Tokenın tipi

<h2> Payload </h2>

{
   "jti": "198f3849-ce23-4876-b1bd-bc9c936eec76",
   "sub": "test@test.com",
   "http://schemas.microsoft.com/ws/2008/06/identity/claims/role":    "Common",
   "nbf": 1525268259,
   "exp": 1525268289,
   "iss": " JWPAPI ",
   "aud": "SampleAudience"
}

* jti : Tokenın benzersiz tanımlayıcısı
* aud : Hedef kitle, yani bu belirtecin kime yönelik olduğu
* iss : Belirteç veren, belirteci yayan uygulama anlamına gelir
* exp : Geçerlilik bitiş tarihi
* nbf : Geçerlilik tarihinin belirtilen tarihten önce olmama durumu

<h2> Signature </h2>

HMACSHA256
(
   base64UrlEncode(header) + "." +
   base64UrlEncode(payload),
   secret
)

Belirteçleri doğrulamak amacıyla kullanılan dijital imza


-- Şifreleme algoritması kullanılarak Header - Payload ve secret bölümlerinin nokta ile birleştirilmesi sonucu oluşan benzersiz jwt
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJqdGkiOiIxOThmMzg0OS1jZTIzLTQ4NzYtYjFiZC1iYzljOTM2ZWVjNzYiLCJzdWIiOiJ0ZXN0QHRlc3QuY29tIiwiaHR0cDovL3NjaGVtYXMubWljcm9zb2Z0LmNvbS93cy8yMDA4LzA2L2lkZW50aXR5L2NsYWltcy9yb2xlIjoiQ29tbW9uIiwibmJmIjoxNTI1MjY4MjU5LCJleHAiOjE1MjUyNjgyODksImlzcyI6IlNhbXBsZUlzc3VlciIsImF1ZCI6IkpXUEFQSSJ9.qGImJxUkWzale_IHgIC5s0WRWyetZsShnMuNErXKUe4


Referans : https://medium.com/@evandro.ggomes/json-web-token-authentication-with-asp-net-core-2-0-b074b0cfc870
