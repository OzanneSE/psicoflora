# Como conectar o formulário do site ao Google Forms

Tempo estimado: 15 minutos. Não precisa saber programar.

---

## Por que não usamos o formulário do Psicologia das Pretas

O formulário `CADASTRO DE PACIENTES 1` é a **ficha de triagem** do Psicologia das Pretas.
Ele não serve como primeiro contato da Psicoflora por três motivos:

1. **Oferta diferente.** A ficha fala de psicoterapia semanal de 40 a 50 minutos, com a tabela
   de valores sociais e menção à Psicóloga Priscila. A Psicoflora é consulta integrativa de 1 hora.
   Quem clica em "agendar" na página e cai nessa ficha percebe a incoerência e desiste.
2. **Fricção.** São mais de 20 perguntas obrigatórias. Como primeiro passo de alguém que acabou de
   conhecer o trabalho, é muita coisa — a maior parte abandona no meio.
3. **Dados sensíveis cedo demais.** Contato de emergência, deficiência, identidade LGBTQIAPN+ e
   faixa de renda são dados sensíveis pela LGPD. Pedir isso antes de qualquer conversa é
   desproporcional. O princípio de minimização diz para coletar só o necessário a cada etapa.

**A estrutura certa é em duas etapas:** o site captura 5 informações → a Mari responde e qualifica →
só então envia a ficha completa de triagem.

---

## Passo 1 — Criar o formulário curto da Psicoflora

Em [forms.google.com](https://forms.google.com), crie um formulário em branco chamado
**Psicoflora — Primeiro contato** com exatamente estas 6 perguntas, **nesta ordem**:

| # | Pergunta | Tipo | Obrigatória |
|---|----------|------|-------------|
| 1 | Nome | Resposta curta | Sim |
| 2 | E-mail | Resposta curta | Sim |
| 3 | WhatsApp | Resposta curta | Sim |
| 4 | O que você procura? | Múltipla escolha | Sim |
| 5 | Preferência de atendimento | Múltipla escolha | Não |
| 6 | Relato | Parágrafo | Não |

**Opções da pergunta 4** — copie exatamente assim, com a mesma grafia do site:

- `Consulta em Naturopatia e Fitoterapia`
- `Acompanhamento Integrativo`
- `Ainda não sei — quero entender melhor`

**Opções da pergunta 5:**

- `Online`
- `Presencial`
- `Tanto faz`

> Se o texto das opções não bater exatamente com o do site, a resposta chega em branco na planilha.

Em **Configurações**, deixe desmarcado "Coletar endereços de e-mail" (o e-mail já é a pergunta 2)
e desmarcado "Limitar a 1 resposta" (isso exigiria login do Google e derrubaria a conversão).

---

## Passo 2 — Pegar o código do formulário

1. Clique em **Enviar** → ícone de link (🔗) → **Copiar**.
2. O link se parece com isto:

```
https://docs.google.com/forms/d/e/1FAIpQLSeABC123xyz.../viewform
```

3. O que interessa é o trecho **entre `/e/` e `/viewform`**:

```
1FAIpQLSeABC123xyz...
```

Guarde esse código. Ele é o `id`.

---

## Passo 3 — Pegar o código de cada pergunta

Cada pergunta do Google Forms tem um código próprio, no formato `entry.1234567890`.

1. Abra o formulário na visualização de quem responde (o link do passo 2).
2. Clique com o botão direito em qualquer lugar da página → **Exibir código-fonte da página**
   (ou aperte `Ctrl + U`; no Mac, `Cmd + Option + U`).
3. Na página de código que abrir, aperte `Ctrl + F` e busque por: `entry.`
4. Você verá vários resultados como `"entry.1846102938"`. Eles aparecem **na mesma ordem das
   perguntas do formulário**.
5. Anote os 6 primeiros, em ordem:

```
1º entry............ Nome
2º entry............ E-mail
3º entry............ WhatsApp
4º entry............ O que você procura?
5º entry............ Preferência
6º entry............ Relato
```

> **Alternativa mais simples:** existe a extensão gratuita *Google Forms Entry ID Finder* para
> Chrome, que mostra os códigos numa lista pronta. Se a busca no código-fonte parecer complicada,
> use ela.

---

## Passo 4 — Colar tudo no site

Abra o arquivo `index.html` num editor de texto (Bloco de Notas serve). Aperte `Ctrl + F` e busque
por `CONFIGURAÇÃO DO GOOGLE FORMS`. Você vai encontrar este trecho:

```js
var GOOGLE_FORM = {
  id: '',
  campos: {
    nome:        '',
    email:       '',
    tel:         '',
    interesse:   '',
    preferencia: '',
    relato:      ''
  }
};
```

Preencha entre as aspas, ficando assim (os números são só exemplo — use os seus):

```js
var GOOGLE_FORM = {
  id: '1FAIpQLSeABC123xyz',
  campos: {
    nome:        'entry.1846102938',
    email:       'entry.0293847561',
    tel:         'entry.1102938475',
    interesse:   'entry.9988776655',
    preferencia: 'entry.4455667788',
    relato:      'entry.1029384756'
  }
};
```

Salve o arquivo. Pronto — o formulário do site passa a gravar direto na planilha do Google, com a
cara da Psicoflora. A visitante nem percebe que por trás é um Google Forms.

---

## Passo 5 — Testar antes de divulgar

1. Abra o site e preencha o formulário com os seus próprios dados.
2. Abra o Google Forms → aba **Respostas**. Sua resposta de teste deve estar lá, com todos os
   campos preenchidos e nenhum em branco.
3. Se algum campo vier vazio, o `entry.` daquela pergunta está trocado. Confira a ordem no passo 3.
4. No Google Forms, clique no ícone verde de planilha para receber tudo numa planilha organizada.
5. Ative a notificação por e-mail: aba **Respostas** → menu de três pontinhos → **Receber
   notificações por e-mail de novas respostas**. Assim a Mari é avisada na hora.

**Enquanto não configurar:** o site funciona normalmente e mostra a mensagem de sucesso, mas nada é
enviado. Nesse modo aparece um aviso no console do navegador. Configure antes de divulgar o link.

---

## Passo 6 — A ficha completa, depois

A ficha longa continua tendo o papel dela. O fluxo sugerido:

1. Pessoa preenche os 5 campos no site.
2. Mari recebe a notificação e responde pelo WhatsApp em até 24h.
3. Havendo encaixe, Mari envia a **ficha de anamnese completa da Psicoflora** — que deve ser uma
   versão própria, com as perguntas da consulta integrativa (histórico de saúde, exames recentes,
   medicações em uso, sono, alimentação, diagnósticos), e não a ficha do Psicologia das Pretas.
4. Só então marca a consulta.

Vale criar essa ficha de anamnese própria quando sobrar um tempo. Posso montar o roteiro de
perguntas dela se quiser.

---

## Ainda pendente na página

Estes pontos estão marcados no `index.html` com o comentário `SUBSTITUIR:` — busque por essa
palavra no arquivo para achar cada um.

- Sobrenome da Mariana e número do CRP (aparecem em 2 lugares: seção "Minha caminhada" e rodapé)
- Valor da consulta e formas de pagamento (seção de atendimentos e FAQ)
- Cidade e bairro do consultório (FAQ)
- E-mail, WhatsApp e Instagram reais (rodapé)
- Depoimentos de pacientes — **leia a observação sobre o Código de Ética do CFP** na própria seção
  antes de publicar qualquer um
- Página de Política de Privacidade (o link já existe no rodapé, apontando para `#`)
