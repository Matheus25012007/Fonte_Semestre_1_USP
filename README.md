# Projeto-Eletronica-USP

Projeto desenvolvido para a disciplina de Eletrônica.

## Instruções

Construção de uma fonte retificadora capaz de transformar corrente alternada de tensão eficaz de 127 volts (pico de 179,6 volts) em uma corrente contínua, com valor de tensão ajustável entre 3 e 12 volts.

Teremos a partir da tomada: tensão 127 volts, corrente alternada e frequência de 60 Hz.

## Escolha dos componentes

| Quantidade | Componentes | Valor R$ |
|---|---|---|
| 10x | Resistor 1W 4k7 5% Carvão Phoenix | R$ 0,40 x 10 = R$ 4,00 |
| 10x | Resistor 1W 3k9 5% Metal Filme | R$ 0,40 x 10 = R$ 4,00 |
| 10x | Resistor 1W 1k 5% Metal Filme | R$ 0,40 x 10 = R$ 4,00 |
| 10x | Resistor 1W 120R 5% Metal Filme | R$ 0,40 x 10 = R$ 4,00 |
| 10x | Diodo Retificador 1N4007 (equivalente 1N4004) | R$ 0,20 x 10 = R$ 2,00 |
| 1x | LED 5mm Vermelho Difuso | R$ 0,50 |
| 10x | Resistor 1W 2k2 5% Metal Filme | R$ 0,40 x 10 = R$ 4,00 |
| 2x | Diodo Zener 13V 1W (equivalente 1N4743) | R$ 0,50 x 2 = R$ 1,00 |
| 1x | Protoboard BB-01 400 pontos c/ base | R$ 23,80 |
| 2x | Transistor TIP122 NPN Darlington TO-220 | R$ 4,00 x 2 = R$ 8,00 |
| 2x | Fusível 20AG 1A Vidro | R$ 1,50 x 2 = R$ 3,00 |
| 1x | Potenciômetro 1W B5K (5kΩ) | R$ 7,00 |
| 1x | Capacitor Eletrolítico 470uF x 35V | R$ 2,80 |
| **Total** | | **R$ 68,10** |

> A nota fiscal original dos componentes está disponível em [`nota_fiscal.png`](nota_fiscal.png).

O transformador e o varistor de proteção contra surtos, utilizados na etapa de entrada do circuito, foram reaproveitados de aquisições anteriores do grupo e por isso não constam na nota fiscal acima — suas funções, no entanto, seguem descritas normalmente a seguir.

## Os componentes

**Transformador:** primeiro componente do circuito após a fonte de corrente alternada (tomada). É responsável por reduzir a ddp proveniente da tomada (127V) para um valor próximo ao desejado pelo projeto na saída (3-12V).

Obs.: o transformador apenas altera o valor da diferença de potencial entre seus terminais, não alterando a corrente alternada para corrente contínua.

**Fusível:** dispositivo de segurança que impede a passagem de correntes muito altas, protegendo os dispositivos do circuito em eventuais picos de corrente.

**Varistor:** dispositivo de segurança que, em conjunto com o fusível, protege contra sobretensão da rede.

**Ponte retificadora (diodos 1N4007):** quatro diodos 1N4007 dispostos em ponte completa, utilizados para que o circuito seja abastecido com corrente em ambos os ciclos da corrente alternada, convertendo-a em corrente pulsante unidirecional.

**Capacitor (470uF):** armazena a carga durante os ciclos da corrente alternada, liberando corrente quando a tensão interna é maior que a tensão vinda da fonte, e descarregando quando ocorre a inversão de ciclo, suavizando o ripple da tensão retificada. O capacitor foi dimensionado para um ripple de 10%, chegando a um valor calculado próximo de 458uF; foi escolhido o valor comercial mais próximo, de 470uF.

**Diodo Zener (13V):** regulador de tensão máxima. Somente conduz corrente quando a tensão que chega alcança a tensão nominal do diodo, que no caso deste projeto é de 13V. Se a tensão for menor do que 13V o diodo não conduz e, portanto, não interfere no circuito; se for maior, deixa a corrente passar, mantendo a tensão de referência estável naquele ponto e protegendo o transistor de regulação contra tensões excessivas na base.

**Resistores (4k7, 3k9, 1k, 2k2, 120R):** complementam o circuito de forma a limitar a corrente e polarizar corretamente o LED indicador, o diodo Zener e o transistor, impedindo que a corrente ultrapasse os valores limites dos componentes.

**Potenciômetro (5k):** resistor variável que, em conjunto com o divisor de tensão formado pelos resistores, permite o ajuste da tensão de referência na base do transistor e, consequentemente, o controle do valor da tensão de saída entre 3 e 12 volts.

**Transistor TIP122 (Darlington NPN):** utilizado como elemento de passagem (série), permite o controle da corrente entregue à carga de forma proporcional à tensão ajustada pelo potenciômetro. Por se tratar de um par Darlington, o TIP122 oferece um ganho de corrente muito maior que um transistor comum, suportando correntes de saída mais elevadas com boa capacidade de dissipação térmica (encapsulamento TO-220).

**LED indicador:** sinaliza visualmente que a fonte está energizada e em funcionamento.

## Imagem do circuito

![Esquemático do circuito no EasyEDA](assets/esquematico_easyeda.png)

## Cálculo do capacitor

Para um ripple de tensão de 10% na saída do retificador em ponte completa (frequência de ripple de 120 Hz, o dobro da rede de 60 Hz), a capacitância mínima necessária foi calculada e resultou em um valor próximo de 458uF. O valor comercial mais próximo disponível é 470uF, adotado no projeto.

## Link do circuito no Falstad

A simulação completa do circuito (arquivo exportado do CircuitJS/Falstad) está disponível em [`simulacao_falstad.txt`](simulacao_falstad.txt). Para visualizá-la, basta importar o conteúdo do arquivo em [https://www.falstad.com/circuit/](https://www.falstad.com/circuit/) através da opção *Import From Text*.

## Imagem esquemático da PCB

![Layout da PCB no EasyEDA](assets/pcb_layout_easyeda.png)

## Arquivos da PCB para fabricação

Os arquivos com o desenho das camadas da placa, gerados a partir do EasyEDA e utilizados como molde para a fabricação da PCB, estão disponíveis em:

- [`PCB_Fonte_gerber_camada1.pdf`](PCB_Fonte_gerber_camada1.pdf)
- [`PCB_Fonte_gerber_camada2.pdf`](PCB_Fonte_gerber_camada2.pdf)

## Vídeo no Youtube

Link: https://youtu.be/yVW4G5obYL8 

## Alunos:

- Pedro Henrique Costa Teixeira
- Enzo Ivanaga Marinho
- Matheus Mancilha Marinho
- Emerson Davi de Castro Ferreira

## Agradecimentos

Agradecemos ao excelentíssimo professor Eduardo do Valle Simões, o Rei.
