# 🪄 Fundo Mágico (Magic Background)

O **Fundo Mágico** é uma aplicação web interativa que permite aos usuários gerarem backgrounds customizados utilizando Inteligência Artificial. Basta descrever a ideia do background desejado, e a magia acontece: o sistema gera os códigos HTML/CSS necessários e aplica o resultado em tempo real diretamente na página.

---

## 🚀 Como Funciona?

1. **Descrição:** O usuário digita no formulário o tipo de background que deseja (ex: *"Crie um degradê moderno de roxo para azul com efeito de ondas"*).
2. **Requisição:** Ao clicar no botão "Gerar Fundo Mágico", um script JavaScript captura o evento e faz um envio assíncrono (`POST`) contendo a descrição para um webhook configurado no **n8n** (`https://fbndev.app.n8n.cloud/webhook/56602a93-e9f1-465f-a79b-81ce929f9bbe`).
3. **Processamento (n8n + IA):** O n8n recebe a descrição, processa através de uma IA para estruturar e gerar os blocos de HTML e CSS correspondentes.
4. **Aplicação Dinâmica:** 
   - O código HTML gerado é renderizado imediatamente em uma seção de preview.
   - O código CSS gerado é inserido dinamicamente em uma tag `<style>` no cabeçalho (`<head>`) da página, atualizando o background instantaneamente.
   - O código-fonte de ambos (HTML e CSS) é exibido em blocos formatados para que o usuário possa copiar e usar em seus próprios projetos.

---

## 🛠️ Tecnologias Utilizadas

- **HTML5:** Estrutura semântica e acessível.
- **CSS3:** Estilização com design moderno (Glassmorphism, gradientes e tipografia com a fonte *Roboto Mono*).
- **JavaScript (ES6):** Manipulação de DOM, requisições assíncronas (`fetch` / `async-await`) e injeção dinâmica de estilos.
- **Integração Externa:** Webhook no **n8n** para processamento inteligente da descrição por Inteligência Artificial.

---

## 📂 Estrutura do Projeto

Abaixo está a organização das pastas e arquivos do projeto:

```text
devemDobro/
├── index.html            # Estrutura principal da página web
├── readme.md             # Documentação do projeto (este arquivo)
└── src/
    ├── css/
    │   ├── reset.css     # Limpeza das margens e espaçamentos padrão do navegador
    │   ├── estilo.css    # Estilização visual (layouts, cards, botões e formulários)
    │   └── responsivo.css # Ajustes para dispositivos móveis (telas menores que 768px)
    ├── imagens/
    │   └── bg.JPG        # Imagem de fundo padrão da página
    └── js/
        └── index.js      # Lógica e interações JavaScript (consumo de API e renderização de preview)
```

---

## 📝 Detalhes dos Arquivos Principais

### 1. [index.html](file:///c:/Users/fabin/OneDrive/Documentos/devemDobro/index.html)
Define a estrutura semântica da aplicação. Inclui:
* Um formulário contendo uma caixa de texto (`<textarea>`) para a descrição.
* Um botão com efeito gradiente moderno.
* Um elemento `#preview-section` reservado para exibir visualmente o background gerado.
* Uma grade `#code-output` contendo duas caixas para exibição dos códigos gerados (HTML e CSS).

### 2. [src/js/index.js](file:///c:/Users/fabin/OneDrive/Documentos/devemDobro/src/js/index.js)
Gerencia a interatividade do projeto:
* **Prevenção de Recarregamento:** Controla o envio do formulário com `event.preventDefault()`.
* **Feedback Visual (Loading State):** Altera o texto do botão para *"Gerando Background..."* enquanto aguarda o retorno da API.
* **Consumo de API:** Envia a descrição do usuário em JSON e recebe os blocos `{ html, css }`.
* **Injeção de Estilo:** Adiciona dinamicamente uma tag `<style id="dynamic-style">` no `<head>` do documento para aplicar a estilização gerada. Remove qualquer estilo dinâmico anterior antes de aplicar o novo.
* **Tratamento de Erros:** Caso ocorra alguma falha na requisição, exibe mensagens amigáveis de erro nos blocos de código.

### 3. [src/css/estilo.css](file:///c:/Users/fabin/OneDrive/Documentos/devemDobro/src/css/estilo.css)
Aplica a identidade visual do projeto:
* **Tipografia:** Usa a fonte **Roboto Mono** importada via Google Fonts.
* **Layout Responsivo:** Implementa Flexbox para alinhamento e organização dos cards de código.
* **Efeitos de Hover e Transição:** Os botões possuem feedback de foco e hover com efeitos de transição suave e leve elevação vertical (`translateY(-2px)`).
* **Painéis Estilizados:** Caixa de exibição com paleta de cores escura e texto verde claro (`#5eead4`) para simular um editor de código.

### 4. [src/css/responsivo.css](file:///c:/Users/fabin/OneDrive/Documentos/devemDobro/src/css/responsivo.css)
Garante que a interface se adapte a telas menores (smartphones e tablets):
* Redimensiona o título e subtítulo da página.
* Transforma a grade horizontal de códigos em uma pilha vertical de exibição para melhor legibilidade em aparelhos móveis.

---

## 🏃 Como Rodar o Projeto

Como o projeto é construído puramente com tecnologias web nativas (HTML/CSS/JS), você pode executá-lo diretamente em seu navegador:

1. Navegue até a pasta raiz do projeto.
2. Abra o arquivo `index.html` em qualquer navegador moderno (como Google Chrome, Firefox, Microsoft Edge ou Safari).
   - *Dica:* Você também pode utilizar extensões como o **Live Server** no VS Code para rodar um servidor de desenvolvimento local.
3. Digite uma descrição no campo de texto e clique em **Gerar Fundo Mágico** para testar a integração.
