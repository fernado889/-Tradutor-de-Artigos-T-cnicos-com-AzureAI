# -Tradutor-de-Artigos-T-cnicos-com-AzureAI
pip install requests
import requests
import json

# Substitua com sua chave de API e endpoint
api_key = "SUA_CHAVE_DE_API"
endpoint = "SEU_ENDPOINT"

# URL do endpoint de tradução
url = f"{endpoint}/translate?api-version=3.0&to=pt"  # Alvo: português

# Texto a ser traduzido
text_to_translate = "This is a technical article about Azure AI."

# Preparar o corpo da requisição
body = [{
    "text": text_to_translate
}]

# Definir os cabeçalhos da requisição
headers = {
    "Ocp-Apim-Subscription-Key": api_key,
    "Content-Type": "application/json"
}

# Fazer a requisição de tradução
response = requests.post(url, headers=headers, json=body)

# Verificar a resposta
if response.status_code == 200:
    translation = response.json()
    translated_text = translation[0]['translations'][0]['text']
    print("Texto traduzido:", translated_text)
else:
    print("Erro na tradução:", response.status_code, response.text)
