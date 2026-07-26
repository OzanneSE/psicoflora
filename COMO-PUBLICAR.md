# Como publicar o site — versão sem complicação

Você não precisa criar pasta nenhuma. Esqueça o `index.html` e a pasta `img` por enquanto.

Use só este arquivo:

```
psicoflora-site-completo.html
```

As cinco fotos estão **dentro** dele. É um arquivo só, de 847 KB. Nada mais é necessário.

> Antes de qualquer coisa: dê dois cliques nesse arquivo. Ele abre no navegador e mostra o site
> pronto, com as fotos. Se abriu certo aí, vai abrir certo na internet.

---

## Publicando no GitHub pelo navegador

1. Abra o seu repositório no GitHub.
2. Clique no botão **Add file** → **Upload files**.
3. Arraste o arquivo `psicoflora-site-completo.html` para dentro da área pontilhada.
4. **Renomeie o arquivo para `index.html`.** Isso é importante: o GitHub Pages procura por um
   arquivo com esse nome exato para saber qual é a página inicial.
   - Para renomear antes de subir: clique com o botão direito no arquivo, no seu computador, e
     escolha *Renomear*.
   - Se já subiu com o nome comprido, clique no arquivo dentro do GitHub, depois no ícone de lápis
     (*Edit*), e mude o nome no campo do topo.
5. Role até o fim da página e clique no botão verde **Commit changes**.

Pronto, o arquivo está no repositório.

---

## Ligando o site

1. Ainda no repositório, clique em **Settings** (no menu do topo).
2. Na coluna da esquerda, clique em **Pages**.
3. Em *Source*, escolha **Deploy from a branch**.
4. Em *Branch*, escolha **main** e, ao lado, **/ (root)**. Clique em **Save**.
5. Espere de 1 a 3 minutos e atualize a página.

O endereço do site aparece no topo dessa mesma tela, num quadro verde. Vai ser algo como:

```
https://seu-usuario.github.io/nome-do-repositorio/
```

Esse é o link para mandar para a Mari.

---

## Se preferir o GitHub Desktop

Ele resolve a questão das pastas sozinho — você não precisa criar nada.

1. Abra o GitHub Desktop.
2. Menu **File** → **Add local repository**.
3. Aponte para a pasta onde estão os arquivos. Ele reconhece que já é um repositório.
4. No campo **Remote**, em *Repository settings*, cole o endereço do repositório que você criou.
5. Clique em **Push origin**.

Nesse caminho pode usar o `index.html` original com a pasta `img` — o GitHub Desktop envia a
estrutura inteira automaticamente, e o site fica mais leve para quem acessa.

---

## Qual dos dois usar

| | Arquivo único | `index.html` + pasta `img` |
|---|---|---|
| Precisa criar pasta | Não | Sim |
| Peso para quem acessa | 847 KB de uma vez | 68 KB primeiro, fotos conforme rola a página |
| Trocar uma foto depois | Preciso refazer o arquivo | Você troca só a foto na pasta |
| Melhor para | Publicar hoje, sem travar | Manutenção a longo prazo |

**Sugestão:** publique agora com o arquivo único, para o site sair do papel. Quando quiser mexer nas
fotos, a gente migra para a versão com pasta — é rápido e eu faço a conversão.

---

## Depois que estiver no ar

Me mande o endereço. Faltam dois retoques que só dá para fazer com o link em mãos:

- O campo `"url"` dos dados estruturados, que ajuda o Google a entender o site
- A imagem de pré-visualização (`og:image`), que é a foto que aparece quando alguém compartilha o
  link no WhatsApp ou no Instagram — hoje o link aparece sem imagem
