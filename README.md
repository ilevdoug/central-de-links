# Central de links

Página estática em português do Brasil com três acessos externos, construída somente com HTML5 e CSS. Funciona sem JavaScript e não usa dependências, coleta de dados ou processo de build.

## Visualizar localmente

Na pasta deste projeto, usando Python 3 já instalado:

```sh
python3 -m http.server 8000 --bind 127.0.0.1
```

Abra <http://127.0.0.1:8000/>. Para simular o subdiretório do GitHub Pages, execute o mesmo comando na pasta que contém `central-de-links` e abra <http://127.0.0.1:8000/central-de-links/>. Encerre o servidor com Ctrl+C.

## Editar

- Textos, títulos, domínios e links: `index.html`.
- Cores: variáveis no início de `styles.css`; espaçamentos e layout ficam no mesmo arquivo.
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

## Atualizar

Revise as alterações e envie apenas os arquivos do projeto:

```sh
git diff --check
git diff
git add index.html styles.css .nojekyll .gitignore README.md
git commit -m "Atualiza central de links"
git push origin main
```

Depois, acompanhe a implantação no GitHub e abra a URL indicada em Settings → Pages.

## Verificar problemas

- Em Settings → Pages, confirme a branch `main` e a pasta `/(root)`.
- Confira o resultado da implantação e a mensagem real de erro na aba Actions, que pode exibir a implantação automática do Pages mesmo sem workflow próprio.
- Em caso de 404, confirme `index.html` na raiz e aguarde a conclusão da implantação.
- Se o estilo não carregar, confira `./styles.css`, a capitalização do nome e a resposta HTTP desse arquivo no mesmo subdiretório da página.
- Teste a página em 360 px e 1280 px, percorra os links com Tab e confira os destinos. Os botões são links HTML reais que abrem uma nova aba.
- A indisponibilidade de um site externo não altera o link nem indica defeito nesta página. Não substitua os endereços.

## Estado de publicação

Repositório público criado: <https://github.com/ilevdoug/central-de-links>, branch `main`. Remote local: `https://github.com/ilevdoug/central-de-links.git`. A integração GitHub confirmou a conta `ilevdoug`, mas recusou a escrita com HTTP 403 (`Resource not accessible by integration`). Por isso, os arquivos são enviados por commits na interface autenticada do GitHub. O GitHub CLI e uma credencial para `git push` local não estão disponíveis. A implantação do Pages ainda precisa ser confirmada; este texto não anuncia publicação concluída.

## Verificações executadas em 28/10/2026

- Existência dos cinco arquivos, `.nojekyll` vazio e referência `./styles.css`: aprovados.
- Leitura do HTML com parser: os três destinos decodificados correspondem exatamente aos originais, na ordem correta; `target="_blank"` e `rel="noopener noreferrer"` presentes.
- Ausência de scripts, eventos JavaScript, formulários, assets externos, dependências e links provisórios: conferida.
- Servidores HTTP temporários com a biblioteca padrão do Python: página e CSS responderam 200, com conteúdo íntegro, na raiz e em `/central-de-links/`.
- Contraste calculado entre textos e fundos: mínimo de 5,89:1; botão normal de 8,71:1.
- O código define uma coluna até 759 px, três colunas acima disso, botões de pelo menos 52 px e foco com contorno de 3 px. Isso foi inspecionado no código, sem confirmação visual.
- Testes visuais em 360 px e 1280 px, rolagem horizontal, foco por Tab, abertura por clique e execução com JavaScript desativado **não foram executados**: não há navegador local executável; o navegador remoto não alcançou o servidor local. A página não contém JavaScript.
- Consultas HTTP HEAD aos destinos originais: `sm8dzy.com` respondeu 200; `npcyog.com` e `gcx27r.com` responderam 403 neste ambiente. Essas respostas não confirmam disponibilidade em outros navegadores; os três endereços foram preservados.
- URL pública e CSS em produção: não testados, pois a publicação está bloqueada pelo acesso ao GitHub.
