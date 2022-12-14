<h2 align="middle">
<img src="https://i.imgur.com/FyuosDs.png" width="200"/>

Hermes
</h2>

### ¿Qué?

Hermes es una librería que ofrece una capa de abstracción para algo que nadie pidió: Peticiones HTTP a la página de [Consultar Espacio Físico](https://artemisa.unbosque.edu.co/serviciosacademicos/EspacioFisico/Interfas/EspaciosFisicosAsigandosReporte.php) de la Universidad El Bosque, lo cual permite interactuar con la información del horario de la gente.

### ¿Por qué?

- Para facilitar la creación de mi aplicación [qclase](https://github.com/cfuendesign/qclase), la cual permite visualizar horarios desde la terminal.
- Sé que a alguien más le va a servir esto y, como miembro de la rama [IEEE Unbosque](https://branch-ieee-ueb.netlify.app/), me gusta crear herramientas [libres](https://www.gnu.org/philosophy/free-sw.html) para la comunidad universitaria.

### ¿Deno?

Sí.

Por ahora esta librería/módulo está escrit@ para ser usad@ en [deno](deno.land/) <img src="https://deno.land/logo.svg?__frsh_c=a8nx5mcy04n0" width="20"/>
, el runtime jurásico con soporte de primera clase para TypeScript. Sin embargo, tengo la intención de publicar esto como un paquete de [npm](https://www.npmjs.com/) para usar tanto en Node.js <img src="https://www.servicepilot.com/images/integration/appservice-nodejs.webp" width="15"/> como en el navegador

### Vale, ¿Cómo?

**En deno** <img src="https://deno.land/logo.svg?__frsh_c=a8nx5mcy04n0" width="20"/>

1. Importa la librería en tu código

```javascript
import { EspacioFisicoSchedule, EspacioFisicoScheduleEvent } from "https://raw.githubusercontent.com/cfuendesign/espaciofisico-hermes/mucho/mod.ts"
```

2. Crea una instancia de la clase `EspacioFisicoSchedule` y pasa al constructor un string, que representa la cédula del estudiante de quien quieres ver el horario. Acto seguido, utiliza el método `getScheduleObject` para obtener los datos

```javascript
const main = async () => {
	console.log(await new EspacioFisicoSchedule("0785996").getScheduleObject())
}

main();
```

El método es [asíncrono](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Statements/async_function), así que debe correrse dentro de una función asíncrona y debe ser precedido por la expresión [await](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Operators/await)

3. Córrelo!

```bash
deno run --allow-net programaBacano.ts 
```

Es necesario correr cualquier programa que utilice Hermes con la bandera `--allow-net` de deno, dado que necesita permiso para hacer peticiones HTTP.

Los datos regresarán en forma de un array de `EspacioFisicoScheduleEvent` (Las clases del estudiante representadas como objetos)

### Roadmap / TODOs
- [x] Que la librería sea utilizable Xd
- [ ] Fechas de inicio y final personalizadas
	Por defecto las fechas de inicio y final de todos los horarios se aproximan al Lunes y Domingo más cercanos, respectivamente

### Vainas que recomiendo leer si quieres hacer algo similar

- [Deno DOM | deno.land](https://deno.land/manual@v1.25.2/jsx_dom/deno_dom)
- [Private class fields | MDN Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes/Private_class_fields)
- [Objetos como valor de retorno de un .map() | StackOverflow](https://stackoverflow.com/questions/47841899/js-map-return-object)
- [AloeDB (Por la estructura del módulo y la documentación) | deno.land](https://deno.land/x/aloedb@0.9.0/mod.ts?s=Database)
- [std (Por lo mismo q AloeDB) | deno.land](https://deno.land/std@0.155.0/collections/mod.ts?source)

