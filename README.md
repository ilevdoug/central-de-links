# Central de links

Página estática em português do Brasil com três acessos externos e identidade visual baseada no **Modelo Ultracolorido V2** (*Tigre Dourado Espelhado em camada independente com quadros adicionais para piscar e saudar + Dragão Ornamental em Jade/Turquesa e Ouro + Plaqueta Imperial "Central de links" + Jardim Noturno de Fantasia com Lanternas, Nuvens em Planos, Flores de Lótus e Reflexos na Água + Cartões em Jade Escuro e Ouro Espelhado com Pergaminho, Baú e Talismã + Controle Acessível de Pausa*). Construída somente com HTML5, CSS3 e assets locais otimizados em `.webp`, funciona sem JavaScript e não usa dependências externas, coleta de dados ou processo de build.

## Visualizar localmente

Na pasta deste projeto, usando Python 3 já instalado:

```sh
python3 -m http.server 8000 --bind 127.0.0.1
```

Abra <http://127.0.0.1:8000/>. Para simular o subdiretório do GitHub Pages, execute o mesmo comando na pasta que contém `central-de-links` e abra <http://127.0.0.1:8000/central-de-links/>. Encerre o servidor com Ctrl+C.

## Editar

- Textos, títulos, domínios, camadas e links: `index.html`.
- Cores, gradientes metálicos, animações e layout: variáveis no início de `styles.css`; espaçamentos e animações ficam no mesmo arquivo.
- Assets otimizados em camadas independentes (`.webp`): pasta `assets/` (`cenario-fundo.webp`, `dragao-jade-ouro.webp`, `tigre-q1-base.webp`, `tigre-q2-aceno.webp`, `tigre-q3-piscar.webp`, `ilustracao-pergaminho.webp`, `ilustracao-bau.webp`, `ilustracao-talisma.webp`).
- Preserve os três endereços fornecidos, na ordem original. No HTML, `&amp;` representa o separador `&`, sem alterar o destino interpretado pelo navegador.
- O CSS usa o caminho relativo `./styles.css` e os assets usam `./assets/...`, compatíveis com a raiz e com subdiretórios.

## Publicar no GitHub Pages

O repositório de destino deve ser público, chamado `central-de-links`, na conta pessoal escolhida, com os arquivos de produção deste projeto na raiz da branch `main`. Não é necessário criar workflow, CNAME ou build.

Com GitHub CLI disponível e autenticado, confira a conta com `gh auth status` e verifique se o nome está livre antes de criar o repositório:

```sh
gh repo create central-de-links --public --source=. --remote=origin --push
```

No GitHub, configure: **Settings → Pages → Build and deployment → Deploy from a branch → main → /(root) → Save**.

A API oficial também pode ativar Pages com `source.branch` igual a `main` e `source.path` igual a `/`. Use o endereço retornado pelo GitHub Pages, aguarde a implantação e confirme que tanto a página quanto `styles.css` respondem corretamente. Este README não confirma que a publicação já ocorreu.

## Atualizar (Rotina Automática de Validação, Commit e Push)

Para cada atualização concluída neste projeto, siga esta rotina padrão:

1. **Verificar GitHub CLI e autenticação (`ilevdoug`):**
   - Executável padrão no Windows: `C:\Program Files\GitHub CLI\gh.exe`.
   - Conferir sessão ativa e configurar credencial Git HTTPS:
     ```powershell
     & "C:\Program Files\GitHub CLI\gh.exe" auth status
     & "C:\Program Files\GitHub CLI\gh.exe" auth setup-git --hostname github.com
     ```
   - Se não estiver autenticado, iniciar login web (`& "C:\Program Files\GitHub CLI\gh.exe" auth login --hostname github.com --git-protocol https --web`) e concluir autorização no navegador.

2. **Executar validações obrigatórias antes do commit:**
   - Conferir com parser os três `href`s interpretados, ordem, parâmetros, `&amp;`, `target="_blank"` e `rel="noopener noreferrer"`.
   - Testar resposta HTTP 200 na raiz `/` e em `/central-de-links/` para HTML, CSS e todos os assets de `./assets/`.
   - Testar larguras de `360 px` e `1280 px`, ausência de rolagem horizontal, altura dos botões (`>= 48 px`), ordem de foco por teclado (`Tab`), contraste WCAG, controle de pausa (`#pausar-animacoes`) e `prefers-reduced-motion: reduce`.

3. **Revisar diff, adicionar somente os arquivos do site pelos nomes e criar commit:**
   - Confirmar que o remote `upstream-site` aponta para `https://github.com/ilevdoug/central-de-links.git`.
   - Não usar `git add .` nem enviar arquivos alheios, credenciais ou assets com redistribuição proibida:
     ```sh
     git diff --check
     git diff
     git add index.html styles.css .nojekyll .gitignore README.md assets/cenario-fundo.webp assets/dragao-jade-ouro.webp assets/tigre-q1-base.webp assets/tigre-q2-aceno.webp assets/tigre-q3-piscar.webp assets/ilustracao-pergaminho.webp assets/ilustracao-bau.webp assets/ilustracao-talisma.webp
     git commit -m "Atualiza central de links com Modelo Ultracolorido V2 e animacoes em camadas"
     git push upstream-site main
     ```

4. **Acompanhar implantação do GitHub Pages e testar produção:**
   - Consultar a implantação com `& "C:\Program Files\GitHub CLI\gh.exe" api repos/ilevdoug/central-de-links/pages/builds/latest` ou `gh run list --repo ilevdoug/central-de-links`.
   - Testar `https://ilevdoug.github.io/central-de-links/` e `https://ilevdoug.github.io/central-de-links/styles.css` após a conclusão do deploy e relatar separadamente commit, push e publicação.

5. **Reversão segura por novo commit (sem reescrever histórico):**
   - SHA da versão inicial antes da evolução temática: `a02897326b4c902c9701869afbd75a632d522371`.
   ```sh
   git checkout a02897326b4c902c9701869afbd75a632d522371 -- index.html styles.css .nojekyll .gitignore README.md
   git commit -m "Reverte central de links para a versao estavel a028973"
   git push upstream-site main
   ```

## Verificar problemas

- Em Settings → Pages, confirme a branch `main` e a pasta `/(root)`.
- Confira o resultado da implantação e a mensagem real de erro na aba Actions, que pode exibir a implantação automática do Pages mesmo sem workflow próprio.
- Em caso de 404, confirme `index.html` na raiz e aguarde a conclusão da implantação.
- Se o estilo não carregar, confira `./styles.css`, a capitalização do nome e a resposta HTTP desse arquivo no mesmo subdiretório da página.
- Teste a página em 360 px e 1280 px, percorra os links com Tab e confira os destinos. Os botões são links HTML reais que abrem uma nova aba.
- A indisponibilidade de um site externo não altera o link nem indica defeito nesta página. Não substitua os endereços.

## Estado de publicação

Repositório público: <https://github.com/ilevdoug/central-de-links>, branch `main`. Remote local (`upstream-site`): `https://github.com/ilevdoug/central-de-links.git`. Site publicado: <https://ilevdoug.github.io/central-de-links/>.

## Verificações executadas em 30/10/2026 (Modelo Ultracolorido V2 — Branch `feat/modelo-ultracolorido-v2`)

- Existência dos arquivos do site (`.gitignore`, `.nojekyll` vazio, `README.md`, `index.html`, `styles.css` e 8 assets `.webp` em `assets/`) e referências relativas `./styles.css` e `./assets/...`: aprovados.
- Leitura do HTML com parser: os três destinos decodificados correspondem exatamente aos originais, na ordem correta; `target="_blank"` e `rel="noopener noreferrer"` presentes nos três CTAs.
- Ausência de scripts, eventos JavaScript, formulários, assets externos, dependências e links provisórios: conferida.
- Servidores HTTP temporários com a biblioteca padrão do Python: página (`15.989 B`), CSS (`20.860 B`) e 8 assets `.webp` (`539.898 B` total) responderam HTTP 200 na raiz `/` e em `/central-de-links/`.
- Contraste WCAG calculado entre textos e fundos: Título H1 vs fundo = `17,44:1`; Título H2 vs cartão jade escuro = `15,87:1`; Domínio vs cartão jade escuro = `14,65:1`; Botão dourado = `9,38:1` (todos nível AAA).
- Testes executados em navegador real (Google Chrome Headless via DevTools Protocol) nas larguras exatas de `360 px` e `1280 px`:
  - Em `360 px`: 1 coluna (`328 px`), `scrollWidth = 360` (ausência de rolagem horizontal), botões com `50 px` de altura (`>= 48 px`).
  - Em `1280 px`: 3 colunas (`338,7 px × 3`), `scrollWidth = 1280` (ausência de rolagem horizontal), botões com `52 px` de altura (`>= 48 px`).
  - Teclado (`Tab #1 → Tab #2 → Tab #3 → Tab #4`): percorreu os três links e o controle de pausa na ordem correta, cada foco exibindo contorno visível de `3px solid rgb(255, 255, 255)`.
  - Controle de pausa (`#pausar-animacoes`) e redução de movimento (`prefers-reduced-motion: reduce`): pausam imediatamente todos os movimentos automáticos sem JavaScript.
