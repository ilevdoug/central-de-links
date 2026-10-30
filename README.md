# Central de links

Página estática em português do Brasil com três acessos externos e identidade visual oriental inspirada em mascotes e interfaces de jogos (*Tigre Guardião da Fortuna + Círculo de Formação de Jade Xianxia + Talismãs Ofuda e Acabamento em Ouro 24k Ultraespelhado*). Construída somente com HTML5 e CSS (incluindo gráficos vetoriais SVG inline), funciona sem JavaScript e não usa dependências externas, coleta de dados ou processo de build.

## Visualizar localmente

Na pasta deste projeto, usando Python 3 já instalado:

```sh
python3 -m http.server 8000 --bind 127.0.0.1
```

Abra <http://127.0.0.1:8000/>. Para simular o subdiretório do GitHub Pages, execute o mesmo comando na pasta que contém `central-de-links` e abra <http://127.0.0.1:8000/central-de-links/>. Encerre o servidor com Ctrl+C.

## Editar

- Textos, títulos, domínios, arte vetorial e links: `index.html`.
- Cores, gradientes metálicos, animações e layout: variáveis no início de `styles.css`; espaçamentos e animações ficam no mesmo arquivo.
- Preserve os três endereços fornecidos, na ordem original. No HTML, `&amp;` representa o separador `&`, sem alterar o destino interpretado pelo navegador.
- O CSS usa o caminho relativo `./styles.css`, compatível com a raiz e com subdiretórios.

## Publicar no GitHub Pages

O repositório de destino deve ser público, chamado `central-de-links`, na conta pessoal escolhida, com os cinco arquivos deste projeto na raiz da branch `main`. Não é necessário criar workflow, CNAME ou build.

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
   - Testar resposta HTTP 200 na raiz `/` e em `/central-de-links/`.
   - Testar larguras de `360 px` e `1280 px`, ausência de rolagem horizontal, altura dos botões (`>= 48 px`), ordem de foco por teclado (`Tab`), contraste WCAG e `prefers-reduced-motion: reduce`.

3. **Revisar diff, adicionar somente os arquivos do site pelos nomes e criar commit:**
   - Confirmar que o remote `upstream-site` aponta para `https://github.com/ilevdoug/central-de-links.git`.
   - Não usar `git add .` nem enviar arquivos alheios, credenciais ou assets com redistribuição proibida:
     ```sh
     git diff --check
     git diff
     git add index.html styles.css .nojekyll .gitignore README.md
     git commit -m "Evolui central de links com direcao artistica oriental hibrida (A+B+C)"
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

## Verificações executadas em 30/10/2026 (Versão Híbrida Oriental A + B + C)

- Existência dos cinco arquivos do site (`.gitignore`, `.nojekyll` vazio, `README.md`, `index.html`, `styles.css`) e referência relativa `./styles.css`: aprovados.
- Leitura do HTML com parser: os três destinos decodificados correspondem exatamente aos originais, na ordem correta; `target="_blank"` e `rel="noopener noreferrer"` presentes nos três CTAs.
- Ausência de scripts, eventos JavaScript, formulários, assets externos, dependências e links provisórios: conferida.
- Servidores HTTP temporários com a biblioteca padrão do Python: página (`18.771 B`) e CSS (`11.850 B`) responderam HTTP 200, com conteúdo íntegro, na raiz `/` e em `/central-de-links/`.
- Contraste WCAG calculado entre textos e fundos: Título H1 vs fundo = `16,54:1`; Título do cartão vs pergaminho = `15,50:1`; Domínio vs pergaminho = `10,76:1`; Botão dourado = `13,60:1` (todos nível AAA).
- Testes executados em navegador real (Google Chrome Headless via DevTools Protocol) nas larguras exatas de `360 px` e `1280 px`:
  - Em `360 px`: 1 coluna (`328 px`), `scrollWidth = 360` (ausência de rolagem horizontal), botões com `54 px` de altura (`>= 48 px`).
  - Em `1280 px`: 3 colunas (`321,3 px × 3`), `scrollWidth = 1280` (ausência de rolagem horizontal), botões com `54 px` de altura (`>= 48 px`).
  - Teclado (`Tab #1 → Tab #2 → Tab #3`): percorreu os três links na ordem correta, cada foco exibindo contorno visível de `3px solid rgb(45, 14, 0)`.
  - Redução de movimento (`prefers-reduced-motion: reduce`): ocultou o reflexo especular (`botao::after { display: none }`) e reduziu a duração das animações a `0,01 ms`.
