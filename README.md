# Gestão de Comissões

Aplicação web (página única, sem servidor) para calcular e acompanhar as comissões de vendas de múltiplas lojas — **Botica**, **Lubotica** e **Loja Digital** — e gerar uma planilha resumida para o setor de RH fechar a folha de pagamento.

Tudo roda direto no navegador: não há backend, banco de dados ou instalação. É só abrir o site.

## O que o site faz

- **Metas financeiras por loja (M1 e M2)**, divididas automaticamente entre as vendedoras cadastradas.
- **4 indicadores configuráveis por loja**, cada um com tipo (R$, %, Quantidade ou Tempo), meta e divisão (individual ou compartilhada entre a equipe).
- **Cálculo automático da comissão** de cada vendedora, combinando o percentual da meta financeira batida com o bônus dos indicadores atingidos.
  - Botica e Lubotica: comissão percentual sobre a venda (0,5% sem meta, 1% na M1, 2% na M2) + 0,25% por indicador batido.
  - Loja Digital: comissão percentual diferente (0% sem meta, 2,5% na M1, 5% na M2) + bônus fixo de R$ 225 por indicador batido.
- **Exportação em PNG** de cada loja, para compartilhar o resultado rapidamente.
- **Exportação em Excel (.xlsx)** com uma aba por loja, trazendo um resumo pronto para a folha de pagamento: metas, configuração dos indicadores, e o valor total a receber por vendedora — já formatado (moeda, percentual, etc.) e com cores por loja.
- Todos os dados ficam salvos no **armazenamento local do navegador** (localStorage) — cada computador/navegador guarda os seus próprios dados.

## ⚠️ Importante sobre os dados

Este site **não tem banco de dados nem servidor**. Os dados digitados (metas, vendedoras, valores de venda, etc.) ficam salvos apenas no navegador de quem está usando, no próprio computador. Isso significa:

- Se você abrir o site em outro computador ou navegador, os dados **não aparecem automaticamente** — cada lugar tem seu próprio armazenamento local.
- Limpar o cache/dados do navegador **apaga os dados salvos**.
- Não há como duas pessoas editarem os mesmos dados ao mesmo tempo e verem as mudanças uma da outra em tempo real.
- Use os botões **Exportar PNG** e **Exportar Excel** para guardar/compartilhar um resultado fora do navegador.

## Como publicar no GitHub Pages

1. Crie um repositório no GitHub (pode ser público ou privado — GitHub Pages funciona em ambos nos planos pagos; em contas gratuitas, precisa ser público).
2. Envie o arquivo `index.html` (e este `README.md`) para o repositório.
3. No repositório, vá em **Settings → Pages**.
4. Em **Branch**, selecione `main` (ou a branch que você usou) e a pasta `/ (root)`. Clique em **Save**.
5. Aguarde 1–2 minutos. O GitHub vai mostrar o link do site publicado, algo como:
   `https://SEU-USUARIO.github.io/gestao-comissoes/`
6. Pronto — esse link já pode ser acessado por qualquer pessoa com internet.

## Atualizando o site depois de publicado

Sempre que quiser alterar alguma regra, texto ou visual do site, basta substituir o arquivo `index.html` no repositório (fazer commit da nova versão). O GitHub Pages atualiza automaticamente em poucos minutos.

## Tecnologia usada

- HTML, CSS e JavaScript puros (sem frameworks, sem processo de build).
- [ExcelJS](https://github.com/exceljs/exceljs) (via CDN) para gerar o arquivo Excel com formatação e cores.
- [html2canvas](https://github.com/niklasvh/html2canvas) (via CDN) para gerar a exportação em PNG.

Como essas bibliotecas são carregadas via internet (CDN), é necessário estar conectado à internet para usar as funções de exportar PNG e exportar Excel — o restante do site (cálculos, cadastro) funciona normalmente offline, uma vez a página carregada.
