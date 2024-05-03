# Relatório de Melhorias
## 1. Posição do Span de Duração do Projeto
Para resolver o problema em que os dias eram atualizados abaixo da barra de rolagem, fizemos as seguintes alterações:

#HTML

'''<span>
    <label id="durationLabel" for="projectDuration">Duração do Projeto em Dias: </label>
    <span id="projectDurationValue">5 dias</span>
</span>
<input type="range" id="projectDuration" min="1" max="30" value="5" oninput="displayValue('projectDurationValue', this.value + (document.getElementById('timeOption').value === 'months' ? ' meses' : ' dias')); calculateProjectCost();">
'''
Agora o <span> para a duração do projeto está posicionado corretamente e exibe a duração conforme o usuário ajusta o controle deslizante.

## 2. Resolvendo o Problema do ‘NaN’

Para evitar que o “NaN” apareça antes de realizar o cálculo, fizemos o seguinte:

# Adicionamos IDs de teste aos botões:

#HTML

<button id="teste" onclick="calculateHourlyRate()">Calcular Custo por Hora</button>
<h3>Custo por Hora: <span id="hourlyRateResult">-</span></h3>

<button id="teste2" onclick="calculateProjectCost()">Calcular Custo do Projeto</button>
<h3>Custo do Projeto: <span id="projectCostResult">-</span></h3>



# No CSS, ocultamos os resultados iniciais:
##CSS

#hourlyRateResult {
    display: none;
}

#projectCostResult {
    display: none;
}


#No JavaScript, adicionamos eventos para os botões:
##JavaScript

const button = document.getElementById('teste');
const h3 = document.getElementById('hourlyRateResult');
const h32 = document.getElementById('projectCostResult');

button.addEventListener('click', function() {
    const estiloAtual = window.getComputedStyle(h3);
    if (estiloAtual.display === 'none') {
        h3.style.display = 'block';
    }
});

const button2 = document.getElementById('teste2');
button2.addEventListener('click', function() {
    const estiloAtual2 = window.getComputedStyle(h32);
    if (estiloAtual2.display === 'none') {
        h32.style.display = 'block';
    }
});

#Agora os resultados devem aparecer corretamente após o cálculo.
