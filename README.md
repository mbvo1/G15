# La Ursa Walk

## Descrição
La Ursa Walk é um projeto que promove caminhadas interativas pela área do Recife Antigo, incentivando a prática de atividade física enquanto proporciona uma experiência educativa sobre os pontos turísticos no bairro do Recife. Usando **Arduino, NFC, LEDs e alertas sonoros**, o projeto guia os participantes durante a caminhada e fornece informações sobre os locais visitados.

### Inicie o Sistema:
Ao ligar o Arduino, o sistema irá iniciar.  
Os LEDs e a caixa de som devem emitir sinais de que o sistema está pronto para iniciar a caminhada.  
Ao iníciar, você deverá colocar um cartão para o NFC reader ler e reconhecer a pessoa já cadastrada. Os LEDs e o som irão ativar, indicando que a caminhada foi iniciada.

### Durante a Caminhada:
A cada ponto turístico que você atingir, o sistema ativará um LED para mostrar que você chegou a um novo local.  
Além disso, a caixa de som emitirá um alerta sonoro e fornecerá informações sobre o ponto turístico atual, como nome e curiosidades.

### Distância:
  O sistema pode ser configurado para contar a distância percorrida ou os pontos turísticos visitados. O NFC ajuda a monitorar seu progresso à medida que você passa por cada ponto de interesse.

### Final da Caminhada:
Ao atingir o ponto final do percurso, o sistema irá exibir a distância total percorrida e finalizar a caminhada.
