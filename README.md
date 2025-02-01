# AluGames - Sistema de Aluguel de Boardgames

Este projeto implementa um sistema de aluguel de boardgames. Ele permite que os usuários visualizem os jogos disponíveis para aluguel, e alterem o status dos jogos entre "Alugar" e "Devolver". O estado do jogo é atualizado tanto na interface gráfica (imagem e botão) quanto no texto exibido ao usuário.

## Funcionalidade

A função `alterarStatus(id)` realiza as seguintes ações:

- Recebe um `id` como argumento para identificar qual jogo foi clicado.
- A função altera dinamicamente a classe de estilo da imagem e do botão, de acordo com o status do jogo (se está alugado ou disponível).
- Quando o jogo está alugado:
  - A imagem do jogo recebe a classe `dashboard__item__img--rented` para indicar que o jogo está alugado.
  - O botão muda de texto para "Devolver" e recebe a classe `dashboard__item__button--return`.
- Quando o jogo está disponível:
  - A imagem remove a classe `dashboard__item__img--rented`, indicando que o jogo não está mais alugado.
  - O botão muda de texto para "Alugar" e remove a classe `dashboard__item__button--return`.

### Código da Função `alterarStatus(id)`

```javascript
function alterarStatus(id) {
    let gameClicado = document.getElementById(`game-${id}`);
    let imagem = gameClicado.querySelector('.dashboard__item__img');
    let botao = gameClicado.querySelector('.dashboard__item__button');

    // Se o jogo já foi alugado
    if (imagem.classList.contains('dashboard__item__img--rented')) {
        // Remove a classe de jogo alugado da imagem
        imagem.classList.remove('dashboard__item__img--rented');
        // Remove a classe 'Devolver' do botão
        botao.classList.remove('dashboard__item__button--return');
        // Altera o texto do botão para "Alugar"
        botao.textContent = 'Alugar';
    } else {
        // Marca a imagem como jogo alugado
        imagem.classList.add('dashboard__item__img--rented');
        // Adiciona a classe 'Devolver' no botão
        botao.classList.add('dashboard__item__button--return');
        // Altera o texto do botão para "Devolver"
        botao.textContent = 'Devolver';
    }
}
