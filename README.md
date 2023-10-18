# 3D_Bot
3d bot with HTML

Esse repositório contém dois arquivos, um HTML e CSS, que juntos explorar a passagem de variáveis CSS pelo HTML, o uso da propriedade de estilo transform-style com o valor preserv-3d, para a criação de objetos com orientação tridimensional sem o uso de nenhum framework, e a utilização de keyframes para juntar tudo e fazer um animação 3D apenas com HTML e CSS.

Apesar de simples, o projeto é interessante de ter sua dinâmica entendida.

<p align="center">
  <img src="https://github.com/Daniel-Alvarenga/3D_Bot/assets/128755697/3a33b8d5-ea2f-4a9e-91f2-8114aeb177eb"/>
</p>


Veja essa div que é responsável por estruturar uma das pernas do robô na animação:

```html
 <div class="leg" id="leg">
    <div class="face" style="--h: 150px; --w: 50px; --tX: 0; --tY: 0; --tZ: 25px; --rX:90deg; --rY: 0deg; --rZ: 0deg;"></div>                                    
    <div class="face" style="--h: 150px; --w: 50px; --tX: 0px; --tY: 0px; --tZ: -25px; --rX:90deg; --rY: 0deg; --rZ: 0deg;"></div>
    <div class="face" style="--t: 50px; --w: 50px; --tX: 0px; --tY: 50px; --tZ: -75px; --rX:0deg; --rY: 0deg; --rZ: 0deg;"></div>
    <div class="face" style="--t: 50px; --w: 50px; --tX: 0px; --tY: 50px; --tZ: 75px; --rX:0deg; --rY: 0deg; --rZ: 0deg;"></div>
    <div class="face" style="--h: 150px; --w: 50px; --tX: 0px; --tY: 0px; --tZ: 25px; --rX:0deg; --rY: 90deg; --rZ: 90deg;"></div>
    <div class="face" style="--h: 150px; --w: 50px; --tX: 0px; --tY: 0px; --tZ: -25px; --rX:0deg; --rY: 90deg; --rZ: 90deg;"></div>
</div>
```
Cada div interna, que é uma face precisa de um certo tamanho, rotação e translação específica, e como se pode ver, cada uma delas possum em seu atributo style, esses valores.
O uso de variáveis assim permite que não seja necessário refereciar cada div no CSS, e usar apenas uma classe que recebe todos esses valores no CSS. Assim, todas as divs responsáveis pela criação de uma única parte, têm seu estilo regido por apenas um bloco css, que usa sua classe para estiliza-las:

```css
.face{
    background-color: var(--faceColor);
    box-shadow: 0 0 7px var(--borderColor);
    border: 1px solid var(--borderColor);
    transform-style: preserve-3d;
    position: absolute;
    width: var(--w); height: var(--h);
    transform: rotateX(var(--rX)) rotateY(var(--rY)) rotateZ(var(--rZ))  translateX(var(--tX)) translateY(var(--tY)) translateZ(var(--tZ));
}
```

Para juntar tudo isso e animar o robô construído, vários keyframes são usados, para animar cada membro do corpo, como esse, responsável por dar vida aos braços:
```css
@keyframes move-arm{
    0%{
        transform: translateX(50px) translateY(50px) translateZ(100px) rotateY(-45deg)
    }
    50%{
        transform: translateX(-50px) translateY(50px) translateZ(75px) rotateY(45deg)
    }
    100%{
        transform: translateX(50px) translateY(50px) translateZ(100px) rotateY(-45deg)
    }
}
```

Se você tiver interesse em visualizar o resultado por completo, pode clonar esse repostório em seu computador e abrir no seu navegador o arquivo index.html
