// script.js

let jogadores = [];
let jogadorAtualIndex = 0;
const cesta = [];
const desafios = [
    "Encontre 3 alimentos ricos em proteína!",
    "Faça uma compra sem ultrapassar R$40,00!",
    "Inclua pelo menos 2 frutas na sua cesta!",
    "Compre 5 itens saudáveis em 5 minutos!",
    "Evite alimentos processados!",
    "Compre 3 itens de diferentes cores!",
    "Faça uma compra apenas com R$20,00!",
    "Adicione 1 lanche saudável e 1 lanche não saudável!",
    "Tente não gastar mais que R$30,00 em 4 produtos!",
    "Escolha pelo menos 3 vegetais para sua cesta!"
];

const perguntas = [
    {
        pergunta: "Qual destes é considerado um grão integral?",
        respostas: ["Arroz Branco", "Arroz Integral"],
        correta: 1,
        pontos: 10
    },
    {
        pergunta: "Frutas são ricas em?",
        respostas: ["Açúcar", "Vitaminas"],
        correta: 1,
        pontos: 10
    },
    {
        pergunta: "Qual alimento é uma fonte de proteína?",
        respostas: ["Maçã", "Peito de Frango"],
        correta: 1,
        pontos: 10
    },
    {
        pergunta: "Qual é a quantidade recomendada de frutas e vegetais que devemos consumir diariamente?",
        respostas: ["1 porção", "3 a 5 porções", "7 a 9 porções"],
        correta: 1,
        pontos: 10
    },
    {
        pergunta: "Qual alimento é uma boa fonte de fibra?",
        respostas: ["Pão Branco", "Aveia"],
        correta: 1,
        pontos: 10
    },
    {
        pergunta: "Qual é a bebida mais saudável para se consumir diariamente?",
        respostas: ["Refrigerante", "Água"],
        correta: 1,
        pontos: 10
    },
    {
        pergunta: "O que é considerado uma 'dieta equilibrada'?",
        respostas: ["Uma dieta rica em açúcar", "Uma dieta rica em frutas, vegetais e grãos integrais"],
        correta: 1,
        pontos: 10
    },
    {
        pergunta: "Qual desses alimentos deve ser consumido com moderação?",
        respostas: ["Legumes", "Alimentos ultraprocessados"],
        correta: 1,
        pontos: 10
    },
    {
        pergunta: "Qual é a importância de consumir fibras?",
        respostas: ["Melhora a digestão", "Aumenta a gordura corporal"],
        correta: 0,
        pontos: 10
    },
    {
        pergunta: "Por que devemos beber bastante água?",
        respostas: ["Ajuda na digestão", "Não tem importância"],
        correta: 0,
        pontos: 10
    }
];

const saldoInicial = 50.00;

// Função para adicionar jogadores
function adicionarJogador() {
    const nome = document.getElementById("nome-jogador").value;
    if (nome) {
        jogadores.push({ nome, saldo: saldoInicial, pontos: 0 });
        document.getElementById("lista-jogadores").innerHTML += `<li>${nome}</li>`;
        document.getElementById("jogador-atual").innerText = nome;
        document.getElementById("nome-jogador").value = '';
        atualizarSaldo();
        atualizarPontos();
    }
}

// Atualiza o saldo e pontos no display
function atualizarSaldo() {
    const saldo = jogadores[jogadorAtualIndex].saldo;
    document.getElementById("saldo").innerText = `Saldo: R$${saldo.toFixed(2)}`;
}

function atualizarPontos() {
    const pontos = jogadores[jogadorAtualIndex].pontos;
    document.getElementById("pontos").innerText = `Pontos: ${pontos}`;
}

// Adiciona produtos à cesta
function adicionarProduto(nome, preco, dica, tipo) {
    const jogador = jogadores[jogadorAtualIndex];

    if (jogador.saldo >= preco) {
        jogador.saldo -= preco;
        cesta.push({ nome, preco, dica, tipo });
        document.getElementById("cesta").innerHTML += `<li>${nome} - R$${preco.toFixed(2)}: ${dica}</li>`;
        document.getElementById("dica").innerText = `Dica: ${dica}`;
        jogador.pontos += 5; // Pontos por adicionar um item
        atualizarPontos();
        verificarDesafio();
        fazerPergunta();
    } else {
        alert("Saldo insuficiente!");
    }

    atualizarSaldo();
}

// Verifica se um desafio deve ser gerado
function verificarDesafio() {
    if (cesta.length % 3 === 0) {
        const desafioIndex = Math.floor(Math.random() * desafios.length);
        document.getElementById("desafio").innerText = desafios[desafioIndex];
    }
}

// Faz uma pergunta
function fazerPergunta() {
    const perguntaIndex = Math.floor(Math.random() * perguntas.length);
    const pergunta = perguntas[perguntaIndex];

    document.getElementById("pergunta-texto").innerText = pergunta.pergunta;
    document.getElementById("resposta1").innerText = pergunta.respostas[0];
    document.getElementById("resposta2").innerText = pergunta.respostas[1];
    document.getElementById("pergunta").style.display = "block";
}

// Responde a pergunta
function responder(respostaIndex) {
    const perguntaIndex = perguntas.findIndex(pergunta => pergunta.pergunta === document.getElementById("pergunta-texto").innerText);
    const pergunta = perguntas[perguntaIndex];

    if (respostaIndex === pergunta.correta) {
        jogadores[jogadorAtualIndex].pontos += pergunta.pontos;
        alert("Resposta correta! Você ganhou " + pergunta.pontos + " pontos.");
    } else {
        alert("Resposta errada! Tente novamente.");
    }

    atualizarPontos();
    document.getElementById("pergunta").style.display = "none";
    jogadorAtualIndex = (jogadorAtualIndex + 1) % jogadores.length; // Passa para o próximo jogador
}

// Girar a roleta
function girarRoleta() {
    document.getElementById("roleta").style.display = "block";
}

// Rodar a roleta
function rodarRoleta() {
    const canvas = document.getElementById("canvas-roleta");
    const ctx = canvas.getContext("2d");
    const premios = [
        { label: "10 Pontos!", value: 10 },
        { label: "Dica sobre Saúde", value: 0 },
        { label: "Itens Especiais!", value: 0 },
        { label: "-5 Pontos!", value: -5 },
        { label: "5 Pontos!", value: 5 },
        { label: "Perde um Turno!", value: 0 }
    ];

    const angulo = Math.floor(Math.random() * 360) + 720; // Faz girar 2 voltas completas
    const premioIndex = Math.floor((angulo % 360) / (360 / premios.length));
    const premio = premios[premioIndex];

    ctx.clearRect(0, 0, canvas.width, canvas.height);
    ctx.beginPath();
    ctx.arc(150, 150, 140, 0, Math.PI * 2);
    ctx.fillStyle = "#f3f3f3";
    ctx.fill();
    ctx.stroke();

    ctx.save();
    ctx.translate(150, 150);
    ctx.rotate((angulo * Math.PI) / 180);
    ctx.fillStyle = "#ffcc00";
    ctx.fillRect(-20, -140, 40, 280);
    ctx.restore();

    // Apresentar o resultado após um tempo
    setTimeout(() => {
        if (premio.value > 0) {
            jogadores[jogadorAtualIndex].pontos += premio.value;
            alert("Você ganhou " + premio.value + " pontos!");
        } else if (premio.label === "Dica sobre Saúde") {
            alert("Dica: Beba bastante água!");
        } else if (premio.label === "Itens Especiais!") {
            alert("Parabéns! Você ganhou um item especial!");
        } else if (premio.value < 0) {
            alert("Você perdeu um turno!");
            jogadorAtualIndex = (jogadorAtualIndex + 1) % jogadores.length; // Pula o turno
        }

        atualizarPontos();
        document.getElementById("roleta").style.display = "none";
    }, 3000);
}

// Recomeçar o jogo
function recomeçar() {
    jogadores = [];
    jogadorAtualIndex = 0;
    cesta.length = 0;
    document.getElementById("lista-jogadores").innerHTML = "";
    document.getElementById("cesta").innerHTML = "";
    document.getElementById("desafio").innerText = "";
    document.getElementById("dica").innerText = "";
    // Reinicia todos os jogadores com saldo e pontos iguais
    atualizarSaldo();
    document.getElementById("mensagem-final").style.display = "none";
    document.getElementById("game").style.display = "block";
}

// Desenha a roleta ao carregar
document.addEventListener("DOMContentLoaded", () => {
    atualizarSaldo();
    atualizarPontos();
});