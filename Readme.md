# API de download de videos do Twitter usando credenciais de login (usuário e senha)

## 📍 Instruções:
- instale as dependencias
- preencha o `.env.example` com seu usuario e senha do Twitter e renomeie para `.env`
- execute a api com `python api.py`
- Endpoint: `http://localhost:5000/baixar`

<br>

## 📍 Exemplo de requisição em Python:

```python
import requests
import json

reqUrl = "http://localhost:5000/baixar"

headersList = {
 "Accept": "*/*",
 "Content-Type": "application/json" 
}

payload = json.dumps({
    "url": "http://twitter.com/i/status/1674901021296934913"
    })

response = requests.request("POST", reqUrl, data=payload,  headers=headersList)

print(response.text)

```

## 📍 Exemplo de requisição em cURL:

```curl
curl  -X POST \
  'http://localhost:5000/baixar' \
  --header 'Accept: */*' \
  --header 'Content-Type: application/json' \
  --data-raw '{"url": "http://twitter.com/i/status/167490102129693491"}'
```

## 📍 Retorno Sucesso ✅ 200:
```json
{
  "file": "http://localhost:5000/download/13aeb4b2bff7.mp4"
}
```

## 📍 Retorno Erro ❌ 4xx/5xx:
```json
{
  "error": "erro ao baixar"
}
```
```json
{
  "error": "URL inválida"
}
```
<br>
<br>

### *Projeto feito com as Libs **Flask** e **yt-dlp***