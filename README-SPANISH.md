# Meme v.2
Colaboradores: Yuri Victor, Joshua Benton, Matt Montgomery, Ivar Vong, Steve Peters, Flip Stewart, Greg MacWilliam.
Meme es un generador que Vox Media utiliza para crear imágenes de uso compartido social. Ver la versión de trabajo en [http://www.sbnation.com/a/meme](http://www.sbnation.com/a/meme).

![screenshot](readme.png)

## ¿Qué hay de nuevo en la versión 2.0?
• Refactorizado en una aplicación formal MV*.

• Corrección de errores con el estado de representación y la repetición de arrastrar y soltar imágenes.

• Mejora en la representación inicial con fuentes web cargadas.

• Mejoras en las opciones de origen cruzado: tanto para imágenes base64 como para CORS.

• Un editor altamente personalizable (¡y fácilmente!) y opciones de tema.

• Selector de marca de agua.

## Instalación
• `git clone https://github.com/voxmedia/meme.git`

• `bundle install`

• `bundle exec middleman`

Esto iniciará un servidor web local en: `http://localhost:4567/`
## Personalización
### Configuración
La configuración y los controles se configuran a través de `source/javascripts/settings.js.erb`. El [settings file](https://github.com/voxmedia/meme/blob/master/source/javascripts/settings.js.erb) tiene comentarios suficientes para documentar la configuración.
### Fuentes
Incluya sus propias fuentes en `stylesheets/_fonts.scss` y luego agregue sus opciones de fuente al [settings file](https://github.com/voxmedia/meme/blob/master/source/javascripts/settings.js.erb#L12).
### Tema del editor
Establezca la [theme-color variable](https://github.com/voxmedia/meme/blob/master/source/stylesheets/_vars.scss#L3) in `source/stylesheets/_vars.scss`. Ese único color se teñirá en todos los controles del editor.
## Cross-Origin Resources (CORS)
Esta es una aplicación basada en HTML5 Canvas y, por lo tanto, viene con algunas restricciones de seguridad al cargar gráficos a través de dominios (por ejemplo, un elemento de lienzo en *http://tatooine.com* no puede exportarse con una imagen alojada en *http://dagobah.com*).
Si está alojando esta aplicación en el mismo dominio que sirve sus imágenes, ¡entonces felicidades! No tienes problemas. Sin embargo, si está pasando por un CDN, probablemente encontrará algunos problemas de seguridad de cruce de dominio; en ese momento tiene dos opciones:

1. Siga este [excellent MDN article](https://developer.mozilla.org/en-US/docs/Web/HTML/CORS_enabled_image) sobre cómo configurar encabezados "Access-Control-Allow-Origin". Deberá habilitar estos encabezados en su CDN, momento en el cual la aplicación Meme debería poder solicitar imágenes desde él.
2. Inserte todas sus imágenes de marca de agua como URI de datos base64 dentro del archivo `settings.js.erb`. El método helper de uri de datos del pipeline `asset_data_uri` de activos facilita esto, e incrusta efectivamente todos los datos de imagen dentro de su JavaScript. La desventaja aquí es que su JavaScript se convertirá en una carga útil muy grande a medida que incluya más imágenes. A largo plazo, la configuración de los encabezados CORS será una opción mejor.
## Ejemplos
• http://www.sbnation.com/a/meme

• https://twitter.com/voxdotcom/status/481671889094340608

• https://twitter.com/voxdotcom/status/479228288221470721

• https://twitter.com/voxdotcom/status/481619042545844225

## Contribuir
1. Haz un fork ( https://github.com/voxmedia/meme/fork )
2. Crea una nueva rama de características (`git checkout -b my-new-feature`)
3. Realiza el commit de tus cambios (`git commit -am 'Add some feature'`)
4. Haz push en la rama (`git push origin my-new-feature`)
5. Crea una nueva solicitud de extracción