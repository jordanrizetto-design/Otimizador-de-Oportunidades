<img src="buscaloop-logo.svg" alt="BuscaLoop" height="72">

# BuscaLoop

O funil da sua busca de emprego, do posicionamento à conversão em proposta. Funciona com o **Claude gratuito ou com assinatura** (Pro ou Max), e opcionalmente com a API da Anthropic.

Um copiloto de IA gratuito para a busca de emprego: gera prompts prontos para o **Claude.ai — gratuito ou com assinatura** analisar seu perfil do LinkedIn, encontrar vagas, avaliar sua estratégia de busca, melhorar seu currículo, escrever cartas de apresentação e identificar as skills certas para destacar.

Não é um chatbot nem um app — é uma **página estática** (HTML + CSS + JavaScript puro, sem backend, sem build, sem chave de API) que você abre no navegador, preenche formulários curtos e recebe prompts já elaborados para colar no Claude.

## O que ela faz

### Configuração da busca (comece por aqui)

- **Tipo de busca:** Diretoria/C-level/VP, Gerência/Head, Coordenação/Sênior, Pleno/Júnior/Estágio ou Consultoria/interim/conselho.
- **Países de busca:** Brasil, Portugal, Itália, Espanha, Estados Unidos, Canadá, México, Colômbia, Chile, Argentina, Reino Unido, Alemanha, remoto global e outros que você digitar.
- **Idioma das respostas** (português, inglês, espanhol, italiano) e **área/função**.
- **Perfil base:** cargo atual, cargos-alvo, resumo e CV. Preenchido uma vez, ele já entra nos campos de todas as ferramentas.
- **Preencher com meus dados:** cada ferramenta tem esse botão, e o box de configuração tem "Preencher todas as ferramentas". Os dados vêm do Perfil base; o que faltar lá é buscado no primeiro box da página onde você já escreveu aquela informação (cargo, resumo, CV, setor, descrição da vaga, cidade). O que vier de outra ferramenta também é guardado no Perfil base. Campos em que você já escreveu algo são preservados.

### O funil

A página organiza a busca em um funil de cinco etapas. Cada camada mostra as ferramentas daquela etapa e, quando há dados no Rastreador, quantas oportunidades estão nela:

| Etapa | Ferramentas | Contagem do Rastreador |
|---|---|---|
| Posicionamento | Configuração e perfil base, Perfil LinkedIn, Currículo, Skills-chave, Cursos | — |
| Prospecção | Vagas e alertas, Abordagem direta, Consultoria | Mapeada |
| Conversas | Rastreador, Carta de apresentação | Em contato + Candidatura enviada |
| Entrevistas | Assistente executivo, Avaliador de estratégia | Entrevista |
| Proposta (conversão) | Rastreador e Assistente executivo | Proposta |

Com base no tipo de busca, o funil numera por onde começar, reordena as ferramentas e marca as prioritárias:

| Tipo de busca | Prioridades no funil | Por quê |
|---|---|---|
| Diretoria / C-level / VP | Perfil base → Rastreador → Abordagem direta → Perfil LinkedIn → Assistente executivo | A maioria das posições é preenchida por headhunters e rede, muitas sem anúncio |
| Gerência / Head | Perfil LinkedIn → Vagas e alertas → Abordagem direta → Rastreador | Vagas publicadas e rede têm peso parecido |
| Coordenação / Sênior | Vagas e alertas → Currículo → Carta → Rastreador | Busca direta funciona, desde que o CV passe na triagem (ATS) |
| Pleno / Júnior / Estágio | Vagas e alertas → Currículo → Carta → Skills | Volume de candidaturas bem adaptadas é decisivo |
| Consultoria / interim / conselho | Consultoria → Perfil LinkedIn → Abordagem direta → Rastreador | O trabalho é de prospecção e posicionamento |

O tipo de busca, os países e o idioma são acrescentados automaticamente ao final de todos os prompts.

### As 12 ferramentas

| Ferramenta | O que faz |
|---|---|
| Analisador de Perfil do LinkedIn | Avalia headline, "Sobre" e experiências, com reescritas sugeridas |
| Buscador de Oportunidades | Prompt para o Claude pesquisar vagas na web nos países escolhidos, links de busca no LinkedIn por país, **central de alertas** e busca ao vivo opcional via Adzuna |
| Avaliador de Estratégia de Busca | Diagnóstico de canais, volume e conversão, com plano de ação |
| Melhorador de Currículo | Reescrita otimizada para ATS e para a vaga-alvo, com opção de destacar os últimos 10–15 anos |
| Redator de Cartas de Apresentação | Carta específica conectando seu perfil à vaga |
| Identificador de Skills-Chave | Skills a destacar no LinkedIn para cada tipo de vaga |
| **Rastreador de Candidaturas e Contatos** | Funil por status, follow-ups vencidos em destaque, lembretes para Google Agenda/Outlook (.ics), exportação em planilha (.csv) e prompt de revisão semanal |
| **Abordagem Direta e Mercado Oculto** | Mensagens para headhunters, decisores e rede no limite de cada canal, com 2 follow-ups, e links para encontrar headhunters no LinkedIn por país |
| **Consultoria, Interim e Conselho** | Ofertas, proposta de valor, referência de preço pesquisada na web, canais de prospecção e plano de 30 dias |
| **Cursos e Certificações** | Cursos atuais com custo, duração e link, separando o que recrutadores valorizam do que é só "bom ter" |
| **Assistente Executivo da Busca** | Agenda semanal em blocos, metas, follow-ups priorizados (importados do rastreador) e briefing para a próxima conversa importante |
| **12 · Playbook em e-book** (destaque) | Sempre a última ferramenta: junta tudo num e-book com o status de cada passo, recomendações para o que falta e a rotina de revisão a cada 2 semanas. Também tem atalho no funil ("Fechando o loop") |

## Três modos de uso: gratuito, Pro/Max ou API

O **passo 1** do box "Configure sua busca" pede que você escolha **um** dos três modos (obrigatório; dá para trocar a qualquer momento). Enquanto nenhum é escolhido, a página funciona como no modo gratuito:

| Modo | Como funciona | Custo |
|---|---|---|
| **Claude gratuito** (padrão) | A página gera o prompt; você copia e cola no Claude.ai. | Grátis, com limite de mensagens do plano gratuito |
| **Claude Pro ou Max** | Os prompts pedem respostas mais completas (por exemplo, 15 a 25 vagas e entregas em documento). Nas ferramentas de vagas, cursos e consultoria, a página lembra de ativar o modo **Research** no Claude.ai ("+" → Research). | Sua assinatura atual |
| **API da Anthropic** | Um botão "Gerar resposta aqui (API)" mostra a resposta direto na página, com pesquisa na web, fontes, custo de cada resposta e um campo para pedir ajustes. | Pago por uso no Claude Console, à parte da assinatura |

**Sobre o modo API:**
- A assinatura Pro/Max do Claude.ai **não** inclui créditos de API. Crie uma chave no [Claude Console](https://platform.claude.com/) (menu API Keys) e defina um limite de gastos mensal.
- Modelos disponíveis: Claude Sonnet 5.5 (recomendado), Claude Opus 5.5 (mais profundo) e Claude Haiku 4.5 (mais barato). A pesquisa na web custa US$ 10 por mil pesquisas, além dos tokens; cada resposta costuma custar alguns centavos de dólar, e o valor aproximado aparece embaixo dela.
- A chave vai direto do navegador para a API da Anthropic, sem nenhum servidor intermediário. Por padrão ela não fica salva; a opção "Lembrar a chave neste navegador" é para uso em computador pessoal.

**Kit do Projeto BuscaLoop** (funciona também no plano gratuito): copie as instruções do projeto e baixe o arquivo de conhecimento `buscaloop-perfil.md`, com sua configuração, perfil, CV e situação do Rastreador. Crie um Projeto "BuscaLoop" no Claude.ai com esses dois itens, e toda conversa do projeto já começa conhecendo você.

## Playbook em e-book (ferramenta 12, em destaque)

O botão **"Gerar meu playbook"** monta um e-book personalizado com tudo o que está salvo no navegador:

1. Como usar o playbook (o ciclo de 2 semanas)
2. Sua configuração (modo de IA, tipo de busca, países, área)
3. Perfil base, campo a campo
4. O funil, etapa por etapa — cada ferramenta com selo **Feito** (data e prazo de revisão), **Pendente** (com recomendação para concluir) ou **Revisão atrasada** (mais de 2 semanas)
5. Central de alertas
6. Rastreador e funil real, com follow-ups vencidos
7. Plano de ação — todos os passos e mudanças pendentes, na ordem recomendada para o tipo de busca, e metas semanais sugeridas
8. Rotina a cada 2 semanas, com as próximas três datas de revisão

Opções: **Salvar em PDF** (abre a janela de impressão), **Baixar e-book (.html)** e **Lembretes de revisão a cada 2 semanas** (arquivo de agenda com 13 revisões quinzenais, cerca de 6 meses). A página registra no navegador quando cada ferramenta foi usada, para o e-book saber o que está feito e o que precisa ser revisado.

## Por que não conecta direto no LinkedIn?

O LinkedIn proíbe, nos seus Termos de Uso, automação e coleta automática de dados por robôs (login automático, scraping, navegação programada) — isso pode levar à **suspensão da conta**. Por isso esta ferramenta não tenta automatizar o LinkedIn. Em vez disso:

- Para o **perfil**: exporte um PDF (no seu perfil, clique em "Recursos" → "Salvar como PDF") e cole o texto no campo indicado, ou copie e cole diretamente da página.
- Para **vagas**: copie e cole a descrição da vaga que te interessa.
- Para **buscar vagas novas**: o Claude.ai tem busca na web integrada (inclusive no plano gratuito), então a ferramenta 2 pede a ele que pesquise vagas atuais em portais abertos.

Esse fluxo manual é mais seguro e continua 100% funcional — só exige um copiar-e-colar a mais.

## Busca direta no LinkedIn

O Buscador de Oportunidades tem um botão **"Links de busca no LinkedIn"**. Ele não faz login nem coleta dados automaticamente: apenas monta as URLs públicas de busca de vagas do LinkedIn, uma por país escolhido, já filtradas por cargo, senioridade e modalidade. Você abre cada link logado na sua própria conta.

## Central de alertas (sem API)

Para receber vagas novas sem cadastrar nenhuma API, o Buscador de Oportunidades monta uma **central de alertas**: para cada cargo (separe vários por vírgula) e cada país da configuração, ela gera os links oficiais de busca do **LinkedIn**, do **Indeed**, do **Google Alertas** e, no Brasil, da **Gupy** e da **Vagas.com**. Em cada site você ativa o alerta uma única vez:

- **LinkedIn:** ative o alerta de vaga no topo dos resultados e escolha receber diariamente.
- **Indeed:** informe seu e-mail na caixa de receber novas vagas.
- **Gupy:** preencha seu e-mail no campo que aparece nos resultados (recomendações a cada duas semanas).
- **Vagas.com:** com sua conta logada, salve a busca como alerta.
- **Google Alertas:** confira o termo, escolha a frequência e crie o alerta — útil para vagas executivas divulgadas em sites de headhunters e notícias.

Marque "Alertas ativados" em cada combinação para acompanhar o que já configurou (fica salvo no navegador).

## Busca ao vivo de vagas (Adzuna)

Além do prompt para o Claude pesquisar na web, a ferramenta 2 tem um painel que busca vagas reais **direto na página**, sem precisar abrir o Claude, usando a [API pública e gratuita da Adzuna](https://developer.adzuna.com/) — que cobre o Brasil e mais de quinze outros países.

**Como obter suas credenciais (gratuito, ~2 minutos):**
1. Acesse [developer.adzuna.com](https://developer.adzuna.com/) e crie uma conta gratuita.
2. Confirme seu e-mail e acesse o painel — lá estarão seu **App ID** e sua **App Key**.
3. Cole os dois no painel de busca ao vivo do BuscaLoop sempre que for buscar. Eles **não ficam salvos** na página (por segurança e porque este é um site estático, sem servidor) — você cola a cada sessão.

**Limitações a saber:**
- O plano gratuito da Adzuna tem um limite de chamadas por dia (algumas centenas) — suficiente para uso pessoal.
- Como é um agregador de vagas publicadas abertamente, cargos de diretoria/C-level preenchidos por headhunters tendem a aparecer menos do que posições júnior/pleno/sênior publicadas em portais.
- Como suas credenciais são digitadas no navegador e a chamada é feita direto do seu navegador para a Adzuna (sem servidor intermediário), qualquer pessoa com acesso ao seu computador durante a sessão poderia vê-las na aba de rede do navegador. Não compartilhe sua tela com credenciais preenchidas, e não coloque suas credenciais direto no código-fonte de um repositório público — isso as exporia a qualquer pessoa que veja o repositório.

## Como funciona por baixo dos panos

- Um único arquivo `index.html` com CSS e JavaScript embutidos.
- Nenhum backend e nenhuma chave de API obrigatória (a Adzuna e a API da Anthropic são opcionais).
- A configuração, o perfil base, o rastreador e a marcação dos alertas ficam salvos **somente no navegador de quem usa** (localStorage). Não vão para nenhum servidor nem aparecem em outro aparelho. O botão "Apagar meus dados deste navegador" limpa tudo — recomendado em computadores compartilhados.
- Nada é enviado à IA até você mesmo copiar e colar o prompt no Claude.ai.
- Funciona em qualquer hospedagem de arquivo estático (GitHub Pages, Netlify, Vercel, ou até abrindo o arquivo direto no navegador).

## Como publicar no GitHub Pages (passo a passo para iniciantes)

Você não precisa saber usar linha de comando — dá para fazer tudo pelo site do GitHub.

1. **Crie uma conta gratuita** em [github.com](https://github.com), se ainda não tiver.
2. Clique no botão **"+"** no canto superior direito → **"New repository"**.
   - Dê um nome, por exemplo `buscaloop`.
   - Marque como **Public**.
   - Clique em **"Create repository"**.
3. Dentro do repositório recém-criado, clique em **"Add file" → "Upload files"**.
4. Arraste os arquivos deste projeto (`index.html`, `README.md`, `LICENSE` e `buscaloop-logo.svg`) para a área de upload e clique em **"Commit changes"**.
5. Vá em **"Settings"** (nas abas do topo do repositório) → **"Pages"** (menu lateral).
6. Em **"Build and deployment" → "Source"**, selecione **"Deploy from a branch"**.
7. Em **"Branch"**, selecione **`main`** e a pasta **`/ (root)`**, depois clique em **"Save"**.
8. Aguarde 1 a 2 minutos e atualize a página. Vai aparecer um link no formato:
   ```
   https://SEU-USUARIO.github.io/buscaloop/
   ```
   Esse é o endereço público do seu BuscaLoop — pode compartilhar com quem quiser.

## Como usar (guia para quem nunca usou IA)

1. Acesse [claude.ai](https://claude.ai) e crie uma conta gratuita (só precisa de e-mail — sem cartão de crédito).
2. Na página do BuscaLoop, preencha primeiro o painel "Configure sua busca" (tipo de busca, países e perfil base). Depois siga os números do funil, abra uma ferramenta e preencha o formulário com suas informações reais.
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
- Para adicionar uma ferramenta, copie um bloco `<details class="tool" data-id="...">...</details>` existente, ajuste os campos, adicione uma função no objeto `promptBuilders` e inclua o `data-id` nas listas `rota` e `ordem` de cada tipo em `SEARCH_TYPES` e na etapa certa de `FUNNEL_STAGES`, no `<script>`.
- Não esqueça de atualizar o link do GitHub no menu de navegação (`<nav class="links">`) depois de publicar.

## Licença

MIT — veja o arquivo [LICENSE](./LICENSE). Use, copie e adapte livremente.
