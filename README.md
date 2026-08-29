# 🧭 Bússola de Carreira

Um copiloto de IA gratuito para a busca de emprego: gera prompts prontos para o **Claude.ai (plano gratuito)** analisar seu perfil do LinkedIn, encontrar vagas, avaliar sua estratégia de busca, melhorar seu currículo, escrever cartas de apresentação e identificar as skills certas para destacar.

Não é um chatbot nem um app — é uma **página estática** (HTML + CSS + JavaScript puro, sem backend, sem build, sem chave de API) que você abre no navegador, preenche formulários curtos e recebe prompts já elaborados para colar no Claude.

## O que ela faz

| # | Ferramenta | O que gera |
|---|---|---|
| 1 | Analisador de Perfil do LinkedIn | Avaliação da headline, do "Sobre" e das experiências, com reescritas sugeridas |
| 2 | Buscador de Oportunidades | Prompt para o Claude pesquisar vagas na web **+ busca ao vivo via Adzuna + botão que abre a busca oficial do LinkedIn já filtrada** |
| 3 | Avaliador de Estratégia de Busca | Diagnóstico da sua estratégia atual (canais, volume, conversão) e plano de ação |
| 4 | Melhorador de Currículo | Reescrita do CV otimizada para ATS e para a vaga-alvo |
| 5 | Redator de Cartas de Apresentação | Carta específica conectando seu perfil à vaga |
| 6 | Identificador de Skills-Chave | Skills a destacar no LinkedIn para cada tipo de vaga que você está considerando |

## Por que não conecta direto no LinkedIn?

O LinkedIn proíbe, nos seus Termos de Uso, automação e coleta automática de dados por robôs (login automático, scraping, navegação programada) — isso pode levar à **suspensão da conta**. Por isso esta ferramenta não tenta automatizar o LinkedIn. Em vez disso:

- Para o **perfil**: exporte um PDF (no seu perfil, clique em "Recursos" → "Salvar como PDF") e cole o texto no campo indicado, ou copie e cole diretamente da página.
- Para **vagas**: copie e cole a descrição da vaga que te interessa.
- Para **buscar vagas novas**: o Claude.ai tem busca na web integrada (inclusive no plano gratuito), então a ferramenta 2 pede a ele que pesquise vagas atuais em portais abertos.

Esse fluxo manual é mais seguro e continua 100% funcional — só exige um copiar-e-colar a mais.

## Busca direta no LinkedIn

A ferramenta 2 também tem um botão **"Buscar no LinkedIn ↗"**. Ele não faz login nem coleta dados automaticamente — apenas monta a URL pública de busca de vagas do LinkedIn (a mesma que você teria na barra de endereço depois de pesquisar manualmente) já preenchida com o cargo, a localização, a senioridade e a modalidade que você informou, e abre em uma nova aba. Você faz a busca normalmente, logado na sua própria conta, do jeito que o LinkedIn realmente funciona.

## Busca ao vivo de vagas (Adzuna)

Além do prompt para o Claude pesquisar na web, a ferramenta 2 tem um painel que busca vagas reais **direto na página**, sem precisar abrir o Claude, usando a [API pública e gratuita da Adzuna](https://developer.adzuna.com/) — que cobre o Brasil e mais de quinze outros países.

**Como obter suas credenciais (gratuito, ~2 minutos):**
1. Acesse [developer.adzuna.com](https://developer.adzuna.com/) e crie uma conta gratuita.
2. Confirme seu e-mail e acesse o painel — lá estarão seu **App ID** e sua **App Key**.
3. Cole os dois no painel de busca ao vivo da Bússola sempre que for buscar. Eles **não ficam salvos** na página (por segurança e porque este é um site estático, sem servidor) — você cola a cada sessão.

**Limitações a saber:**
- O plano gratuito da Adzuna tem um limite de chamadas por dia (algumas centenas) — suficiente para uso pessoal.
- Como é um agregador de vagas publicadas abertamente, cargos de diretoria/C-level preenchidos por headhunters tendem a aparecer menos do que posições júnior/pleno/sênior publicadas em portais.
- Como suas credenciais são digitadas no navegador e a chamada é feita direto do seu navegador para a Adzuna (sem servidor intermediário), qualquer pessoa com acesso ao seu computador durante a sessão poderia vê-las na aba de rede do navegador. Não compartilhe sua tela com credenciais preenchidas, e não coloque suas credenciais direto no código-fonte de um repositório público — isso as exporia a qualquer pessoa que veja o repositório.

## Como funciona por baixo dos panos

- Um único arquivo `index.html` com CSS e JavaScript embutidos.
- Nenhuma chamada de rede, nenhum backend, nenhuma chave de API.
- Os dados que você digita ficam só no seu navegador; nada é enviado a lugar nenhum até você mesmo copiar e colar no Claude.ai.
- Funciona em qualquer hospedagem de arquivo estático (GitHub Pages, Netlify, Vercel, ou até abrindo o arquivo direto no navegador).

## Como publicar no GitHub Pages (passo a passo para iniciantes)

Você não precisa saber usar linha de comando — dá para fazer tudo pelo site do GitHub.

1. **Crie uma conta gratuita** em [github.com](https://github.com), se ainda não tiver.
2. Clique no botão **"+"** no canto superior direito → **"New repository"**.
   - Dê um nome, por exemplo `bussola-carreira`.
   - Marque como **Public**.
   - Clique em **"Create repository"**.
3. Dentro do repositório recém-criado, clique em **"Add file" → "Upload files"**.
4. Arraste os três arquivos deste projeto (`index.html`, `README.md`, `LICENSE`) para a área de upload e clique em **"Commit changes"**.
5. Vá em **"Settings"** (nas abas do topo do repositório) → **"Pages"** (menu lateral).
6. Em **"Build and deployment" → "Source"**, selecione **"Deploy from a branch"**.
7. Em **"Branch"**, selecione **`main`** e a pasta **`/ (root)`**, depois clique em **"Save"**.
8. Aguarde 1 a 2 minutos e atualize a página. Vai aparecer um link no formato:
   ```
   https://SEU-USUARIO.github.io/bussola-carreira/
   ```
   Esse é o endereço público da sua Bússola de Carreira — pode compartilhar com quem quiser.

## Como usar (guia para quem nunca usou IA)

1. Acesse [claude.ai](https://claude.ai) e crie uma conta gratuita (só precisa de e-mail — sem cartão de crédito).
2. Na página da Bússola, abra uma das 6 ferramentas e preencha o formulário com suas informações reais.
3. Clique em **"Gerar prompt"** — um texto pronto aparece na caixa cinza-escura logo abaixo.
4. Clique em **"Copiar prompt"**.
5. Clique em **"Abrir Claude.ai gratuito"** (ou acesse claude.ai em outra aba), cole o texto na caixa de mensagem e envie.
6. Leia a resposta com calma. Se algo não estiver do jeito que você quer, continue a conversa pedindo ajustes — por exemplo, "deixe mais direto" ou "refaça o item 3 com mais detalhes".
7. Repita o processo para as outras ferramentas conforme for avançando na sua busca.

**Dica:** o plano gratuito do Claude tem um limite de mensagens que se renova após algumas horas. Se atingir o limite, espere um pouco antes de gerar o próximo prompt.

## Avisos importantes

- Os prompts pedem explicitamente à IA para **não inventar** experiências, empresas ou números — e sinalizar com `[QUANTIFICAR]` ou `[CONFIRMAR]` onde faltar informação. Ainda assim, **sempre revise** o resultado final antes de enviar qualquer coisa a um recrutador ou publicar no seu perfil.
- Esta ferramenta não substitui aconselhamento jurídico, de carreira ou de RH profissional — é um ponto de partida para acelerar o seu trabalho.

## Personalizando

- Para trocar cores, fontes ou textos, edite as variáveis CSS no topo do `<style>` em `index.html` (seção `:root`) e os textos correspondentes no HTML.
- Para adicionar uma 7ª ferramenta, copie um bloco `<details class="tool">...</details>` existente, ajuste os campos do formulário e adicione uma função correspondente no objeto `promptBuilders` no `<script>`.
- Não esqueça de atualizar o link do GitHub no menu de navegação (`<nav class="links">`) depois de publicar.

## Licença

MIT — veja o arquivo [LICENSE](./LICENSE). Use, copie e adapte livremente.
