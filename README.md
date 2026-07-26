# Psicoflora — Clínica Integrativa

Site institucional da Psicoflora: psicologia, naturopatia e fitoterapia integradas no atendimento
de **Mariana Rosa — Psicóloga, CRP 05/67623**.

Página única, sem dependências de build. Abrir o `index.html` já mostra o site pronto.

---

## Arquivos

```
index.html            o site inteiro (HTML + CSS + JS num arquivo só)
img/                  fotos otimizadas (JPG + WebP)
GUIA-FORMULARIO.md    como conectar o formulário ao Google Forms
README.md             este arquivo
```

Não há etapa de compilação, `npm install` nem framework. É HTML puro de propósito: qualquer pessoa
consegue editar um texto no Bloco de Notas sem quebrar nada.

---

## Publicar no GitHub Pages

1. Suba os arquivos para o repositório (mantendo a pasta `img/` junto do `index.html`).
2. No GitHub, vá em **Settings** → **Pages**.
3. Em *Source*, escolha **Deploy from a branch**.
4. Em *Branch*, escolha `main` e a pasta `/ (root)`. Clique em **Save**.
5. Aguarde de 1 a 3 minutos. O endereço aparece no topo da mesma página, no formato
   `https://SEU-USUARIO.github.io/NOME-DO-REPOSITORIO/`.

### Domínio próprio (opcional)

Para usar `psicoflora.com.br` em vez do endereço do GitHub:

1. Em **Settings** → **Pages** → *Custom domain*, digite o domínio e salve.
2. No painel de quem registrou o domínio, crie os registros DNS:
   - Quatro registros `A` apontando para `185.199.108.153`, `185.199.109.153`,
     `185.199.110.153` e `185.199.111.153`
   - Um registro `CNAME` de `www` apontando para `SEU-USUARIO.github.io`
3. De volta ao GitHub, marque **Enforce HTTPS** assim que a opção ficar disponível.

---

## Como editar o conteúdo

Abra o `index.html` em qualquer editor de texto. O arquivo é comentado em português, seção por
seção. Para achar um trecho, use `Ctrl + F`:

| Buscar por | Leva até |
|---|---|
| `CONFERIR` | pontos que precisam de confirmação da Mariana |
| `ACRESCENTAR` | dados que ainda não existem (e-mail profissional) |
| `CONTATO DIRETO` | número de WhatsApp e mensagem pré-preenchida |
| `CONFIGURAÇÃO DO GOOGLE FORMS` | ligar o formulário de agendamento |
| `DESIGN SYSTEM` | cores e tipografia da marca |

### Cores da marca

Estão todas no topo do arquivo, em `:root`. Trocar uma cor ali muda o site inteiro.

| Cor | Código | Uso |
|---|---|---|
| Verde Profundo | `#24372a` | títulos e seções escuras |
| Verde Floresta | `#324c37` | botões |
| Verde Musgo | `#5e7461` | detalhes decorativos |
| Off White | `#edeae4` | fundo geral |
| Argila | `#b89b84` | detalhes e numerais |
| Berinjela | `#5e4b68` | frases de destaque |
| Lavanda Botânica | `#a89ab4` | destaques em fundo escuro |

> Verde Musgo puro tem contraste de 4,22:1 sobre o Off White, abaixo do mínimo de 4,5:1 exigido pelo
> WCAG AA para texto pequeno. Por isso existe a variável `--musgo-texto` (`#4e6352`), usada em textos
> e ícones. A cor original segue nos elementos puramente decorativos.

### Tipografia

Averia Sans Libre (Light, Regular e Bold), carregada do Google Fonts, conforme o manual da marca.

---

## Estado atual

**Pronto e no ar:**

- Todas as seções, textos e fotos
- Responsivo, com CTA fixo no rodapé em telas pequenas
- Contraste conferido no padrão WCAG AA
- Imagens otimizadas: 24 MB de originais viraram 2,6 MB, com WebP e JPG de reserva
- Atendimento online posicionado como principal; presencial em Cabo Frio (RJ) como exceção
- Dados estruturados schema.org com atendimento online para todo o Brasil
- WhatsApp com mensagem pré-preenchida como CTA principal

**Pendente:**

- **Formulário de agendamento.** Ainda não está conectado a lugar nenhum. Enquanto o
  `GOOGLE_FORM.id` estiver vazio no `index.html`, a página esconde o formulário automaticamente e
  mostra no lugar o botão de WhatsApp — assim nenhuma mensagem se perde. O passo a passo para ligar
  está no `GUIA-FORMULARIO.md`.
- **E-mail profissional** no rodapé (busque por `ACRESCENTAR`). O WhatsApp já está no ar.
- **Endereço do consultório.** Cabo Frio (RJ) já está no site. Como o presencial é exceção, o
  endereço é combinado no primeiro contato — não precisa aparecer na página.
- **Valor da consulta.** Por opção, a página não exibe preço: informa que o valor é passado no
  primeiro contato. Se preferir mostrar, o lugar é a seção de atendimentos e a pergunta sobre valores.
- **Política de Privacidade.** Necessária antes de o formulário entrar no ar, por causa da LGPD.
- **Endereço do site no JSON-LD.** No topo do `index.html`, o campo `"url"` dos dados estruturados
  está vazio. Preencha com o endereço final assim que o GitHub Pages publicar.
- **Perfil no Google Empresas.** Como o atendimento é majoritariamente online, isso deixa de ser
  prioridade. Vale mais investir em conteúdo e no Instagram, onde o alcance não depende de cidade.

---

## Decisões de conteúdo que valem conhecer

**Nada de promessa de cura.** A página não afirma que o tratamento cura ou leva à remissão de
doenças. A remissão do Hashimoto aparece como história pessoal da Mariana, com a ressalva explícita
de que não é garantia de resultado para ninguém. Além de ser exigência do Código de Ética do CFP e
da regulação de publicidade em saúde, é o que protege quem chega à página em sofrimento.

**Cuidado complementar, nunca substituto.** Em nenhum momento o texto sugere trocar medicação por
plantas ou suplementos. A primeira pergunta das dúvidas frequentes deixa claro que a suspensão de
qualquer medicamento é decisão exclusiva do médico que prescreveu.

**Sem depoimentos.** O Código de Ética do CFP restringe a divulgação de depoimentos e casos clínicos
por psicólogos. No lugar deles entrou a seção "O que esperar da primeira consulta", que reduz a
insegurança de quem nunca fez um atendimento integrativo sem esbarrar na regra. Antes de publicar
qualquer depoimento, vale confirmar o formato permitido junto ao CRP-05.

---

© Psicoflora. Todos os direitos reservados.
