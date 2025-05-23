# vitoriaeduardal('https://fonts.googleapis.com/css2?family=Montserrat:ital,wght@0,100..900;1,100..900&display=swap');

:root {
    --cor-destaque: #ED145B;
    --cor-gradiente-preto: linear-gradient(113deg, #000 0%, #1E2021 44.96%, #1E2022 100%);
}

* {
    margin: 0;
    padding: 0;
    font-family: Montserrat;


    display: flex;
    justify-content: center;
    align-items: center;
    padding: 16px 21px 18px 21px;
    background: var(--cor-gradiente-preto);
    height: 100vh;
    flex-direction: column;
}


.container {
    display: flex;
    width: 65rem;
    flex-direction: column;
    align-items: center;
    gap: 3rem;
    overflow: hidden;
}
const botaoMostraPalavras = document.querySelector("#botao-palavrachave");

botaoMostraPalavras.addEventListener("click", mostraPalavrasChave);

function mostraPalavrasChave() {
  const texto = document.querySelector("#entrada-de-texto").value;

  const campoResultado = document.querySelector("#resultado-palavrachave");

  const palavrasChave = processaTexto(texto);

  campoResultado.textContent = palavrasChave.join(", ");
}

function processaTexto(texto) {
  let palavras = texto.split(/\P{L}+/u);

  const frequencias = contaFrequencias(palavras);

  let ordenadas = Object.keys(frequencias).sort(ordenaPalavra);

  function ordenaPalavra(p1, p2) {
    return frequencias[p2] - frequencias[p1];
  }

  return ordenadas.slice(0, 10);
}

function contaFrequencias(palavras) {
  let frequencias = {};

  for (let i of palavras) {
    frequencias[i] = 0;

    for (let j of palavras) {
      if (i == j) {
        frequencias[i]++;
      }
    }
  }

  return frequencias;
}    color: var(--cor-destaque);
    font-size: 2.5rem;
    justify-content: center;
    margin-bottom: 2rem;
    max-width: 100%;
    max-height: 50vh;
    overflow: auto;
}
