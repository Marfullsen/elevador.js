# elevador.js

[![TestHere](https://img.shields.io/badge/Ver%20aquí-gh%20pages-green)](https://marfullsen.github.io/elevador.js)
[![Forked](https://img.shields.io/badge/Forked%20from-tholman-blue)](https://github.com/tholman/elevator.js)
[![Vanilla JS](http://vanilla-js.com/assets/button.png)](https://www.javascript.com/)

¡Finalmente, un botón de "volver arriba" que se comporta como un ascensor de verdad, añadiendo música de ascensor para calmar la incomodidad que puede producirse cuando se desplaza suavemente a la parte superior de la pantalla!

<p align="center">
  <a href="https://marfullsen.github.io/elevador.js" rel="noopener">
 <img src="./docs/img/triangle.png" alt="Botones de ascensor"></a>
</p>

Esto es algo muy serio, ¡[prueba la demo aquí](https://marfullsen.github.io/elevador.js)! (versión mejorada por Marfullsen).

## ¿Qué es `Elevador.js`?
Elevador.js es una mejora realizada a la librería [Elevator.js](https://github.com/tholman/elevator.js) (nótese la traducción). Esta mejora incluye la traducción al español y añade un cambio de colores además de una animación de movimiento en 180 grados de los triángulos del sitio de presentación.

### Instrucciones

`Elevator.js` es una librería independiente (sin jquery o similares), por lo que su uso es bastante sencillo. Todo el estilo de los elementos depende de ti. `Elevator.js` sólo se encarga de la gestión del audio, y de la funcionalidad del desplazamiento.

#### JavaScript

La librería `Elevator.js` reside dentro del universo de JavaScript, lo que la hace bastante simple.

Tendrás que crear una nueva instancia de `Elevator`, y pasarle algunos elementos de audio.

```html
<!-- JS -->
<script src='elevator.js'></script>

<script>
// Se asume que el script de 'Elevator' está incluido.

window.onload = function() {
  var elevator = new Elevator({
    mainAudio: '/src/to/audio.mp3',
    endAudio: '/src/to/end-audio.mp3'
  });
}

// Ahora puedes ejecutar el elevador ejecuntando la siguiente función.
elevator.elevate();
</script>
```

También puedes añadir una opción "para algún elemento", al hacer click en este elemento se invocará la funcionalidad de "Desplazamiento hacia arriba".
```html
<div class="elevator-button">Volver arriba</div>

<script>
// con el script de Elevator ya incluido en la página.

window.onload = function() {
  var elevator = new Elevator({
    element: document.querySelector('.elevator-button'),
    mainAudio: '/src/to/audio.mp3',
    endAudio: '/src/to/end-audio.mp3'
  });
}
</script>
```

En caso que no quieras desplazarte a la parte superior, puedes especificar un objetivo personalizado añadiendo una opción "targetElement":
```html
<div class="elevator-button">Tomar el ascensor hasta el objetivo</div>

<script>
// Se asume que el script de 'Elevator' está incluido.

window.onload = function() {
  var elevator = new Elevator({
    element: document.querySelector('.elevator-button'),
    targetElement: document.querySelector('#elevator-target'),
    mainAudio: '/src/to/audio.mp3',
    endAudio: '/src/to/end-audio.mp3'
  });
}
</script>
```

Si quieres desplazarte a un punto de la página con un poco de _padding_ (relleno) extra en la parte superior, simplemente añade la opción "verticalPadding":
```html
<div class="elevator-button">Tomar el ascensor hasta el objetivo</div>

<script>
// Se asume que el script de 'Elevator' está incluido.

window.onload = function() {
  var elevator = new Elevator({
    element: document.querySelector('.elevator-button'),
    targetElement: document.querySelector('#elevator-target'),
    verticalPadding: 100,  // en pixeles
    mainAudio: '/src/to/audio.mp3',
    endAudio: '/src/to/end-audio.mp3'
  });
}
</script>
```

Si eres realmente serio (aburrido), no tienes que usar el audio... de igual manera puedes establecer un tiempo fijo para desplazarte a la parte superior
```html
<div class="elevator-button">Volver arriba</div>

<script>
// Se asume que el script de 'Elevator' está incluido.

window.onload = function() {
  var elevator = new Elevator({
    element: document.querySelector('.elevator-button'),
    duration: 1000 // milisegundos
  });
}
</script>
```

Si utilizas elevator.js en combinación con otro código, es posible que quieras utilizar callbacks:
```html
<script>
window.onload = function() {
   new Elevator({
       element: document.querySelector('.elevator-button'),
       mainAudio: '/src/to/audio.mp3',
       endAudio: '/src/to/end-audio.mp3',
       duration: 5000,
       startCallback: function() {
         // se ejecuta cuando el ascensor comienza a moverse.
       },
       endCallback: function() {
         // se ejecuta cuando el ascensor alcanza el nivel esperado.
       }
   });
}
</script>
```

### NPM
El paquete también está disponible a través de [NPM](https://www.npmjs.com/package/elevator.js)

### Licencia

Elevator.js está bajo licencia **MIT**.

El audio de la demo se adquirió a través de [Pond5](https://www.pond5.com/stock-music/11517192/elevator-bossa-nova.html), para usarlo se necesitará adquirir una licensia propia.

Derechos reservados © ~ [Tim Holman](http://tholman.com) ~ timothy.w.holman@gmail.com

### References

- [elevator.js by tholman.com](https://tholman.com/elevator.js/)
- [css3-rotate-animation](https://stackoverflow.com/questions/16771225/css3-rotate-animation)
- [Rotate without JS](https://codepen.io/anon/pen/yNpvxb?editors=1111)
- [Checkbox implementation](https://stackoverflow.com/questions/386281/how-to-implement-select-all-check-box-in-html)
- [Scroll event](https://developer.mozilla.org/es/docs/Web/API/Document/scroll_event)