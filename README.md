# CriptoLab

Site educativo, em português, que demonstra criptografia e descriptografia de texto no próprio navegador.

## Como usar

1. Abra `index.html` em um navegador moderno. Para usar a Web Crypto API, publique o site em HTTPS (o GitHub Pages já oferece HTTPS) ou execute em `localhost`.
2. Digite um texto e uma chave secreta e selecione **Criptografar**.
3. Copie o token e use a mesma chave para descriptografar. O painel de rastreamento mostra os parâmetros usados.

## Como funciona

- **PBKDF2 com SHA-256** deriva uma chave de 256 bits da chave digitada e de um salt aleatório, com 310.000 iterações.
- **AES-256-GCM** cifra e autentica o texto com um IV aleatório.
- O token reúne versão, salt, IV e texto cifrado, codificados em Base64URL. Base64URL é apenas uma codificação, não uma camada de criptografia.
- A descriptografia deriva novamente a chave com o salt do token. AES-GCM rejeita uma chave incorreta ou dados modificados.

Toda a operação ocorre localmente com a Web Crypto API. O site não envia nem persiste textos, chaves ou tokens. Use apenas dados de exemplo: isto é uma demonstração educativa, não um gerenciador de senhas.
