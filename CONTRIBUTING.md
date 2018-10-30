# <a name="contributing"></a>Contribución

Le agradecemos su interés en colaborar con la documentación de Visual Studio.

En este tema, comprobará cuál es el proceso básico para agregar o actualizar el contenido del [sitio de documentación de Visual Studio](https://docs.microsoft.com/visualstudio).

Abordaremos lo siguiente:

* [Proceso de contribución](#process-for-contributing)
* [Lista de comprobación orientativa](#guidance-checklist)
* [Creación de los documentos](#building-the-docs)
* [Contribución a los ejemplos](#contributing-to-samples)
* [Contrato de licencia del colaborador](#contributor-license-agreement)

## <a name="process-for-contributing"></a>Proceso de contribución

**Paso 1:** abra un asunto en el que describa el artículo que quiere redactar y su relación con el contenido existente.
El contenido de la carpeta **docs** se organiza en secciones por área de contenido (por ejemplo, depurador). Determine en qué carpeta deberá incluirse el contenido nuevo. Recabe opiniones sobre su propuesta. 

Si los cambios son pequeños, puede omitir este primer paso.

**Paso 2:** bifurque el repositorio de `MicrosoftDocs/visualstudio-docs`.

**Paso 3:** cree una rama (`branch`) para el artículo.

**Paso 4:** redacte el artículo.

Si es un tema nuevo, puede usar esta [plantilla](./styleguide/template.md) como punto de partida. La plantilla contiene las instrucciones de escritura y la explicación de los metadatos necesarios para cada artículo, como la información del autor.

Vaya a la carpeta correspondiente a la ubicación de la tabla de contenido que se determinó para su artículo en el paso 1.
Esa carpeta contiene los archivos Markdown de todos los artículos incluidos en esa sección. Si es necesario, cree una carpeta para colocar los archivos de su contenido.

Agregue las imágenes y otros recursos estáticos a la subcarpeta denominada **media** (elementos multimedia). Si va a crear una carpeta nueva para el contenido, agregue una carpeta de elementos multimedia a la carpeta nueva.

Asegúrese de seguir la sintaxis de Markdown adecuada. Consulte la [guía de estilo](./styleguide/template.md) para obtener más información.

### <a name="example-structure"></a>Ejemplo de estructura

    docs
      /debugger
          debugging-installed-app-package.md
          /media
              debugging-installed-app-package.png

**Paso 5:** envíe una solicitud de incorporación de cambios (PR) desde su rama a `MicrosoftDocs/visualstudio-docs/master`.

Si su solicitud aborda un asunto existente, agregue la palabra clave `Fixes #Issue_Number` al mensaje de confirmación o a la descripción de la solicitud de incorporación de cambios. De este modo, el asunto podrá cerrarse automáticamente cuando se combine la solicitud. Para obtener más información, consulte [Closing issues via commit messages](https://help.github.com/articles/closing-issues-via-commit-messages/) (Cerrar asuntos mediante mensajes de confirmación).

El equipo de Visual Studio revisará su solicitud y le notificará si el cambio es correcto o si son necesarias otras modificaciones para aprobarlo.

**Paso 6:** realice los cambios necesarios que haya acordado con el equipo en la rama.

Los encargados del mantenimiento combinarán la solicitud con la rama principal una vez que se hayan aplicado los comentarios y el cambio no presente problemas.

Las confirmaciones de la rama principal se insertan en la rama en vivo siguiendo un ritmo determinado. Una vez insertadas, podrá ver su contribución en https://docs.microsoft.com/visualstudio/.

## <a name="dos-and-donts"></a>Qué hacer y qué no hacer

La lista siguiente incluye una serie de reglas orientativas que deben tenerse en cuenta a la hora de colaborar en la documentación de .NET.

- **NO** solicite la incorporación de grandes cambios. En su lugar, registre un asunto e inicie una discusión para que podamos definir un rumbo antes de dedicar una gran cantidad de tiempo.
- **LEA** la [guía de estilo](./styleguide/template.md) y las directrices de [voz y tono](./styleguide/voice-tone.md).
- **USE** la [plantilla](./styleguide/template.md) como punto de partida de trabajo.
- **CREE** una rama independiente en la bifurcación antes de trabajar en los artículos.
- **SIGA** el [flujo de trabajo de GitHub](https://guides.github.com/introduction/flow/).
- **HABLE** de sus contribuciones con frecuencia en blogs o Twitter (o cualquier otra red social).

> [!NOTE]
> Es posible que observe que algunos de los temas no siguen actualmente todas las directrices que se especifican aquí y en la [guía de estilo](./styleguide/template.md), pero estamos trabajando para dar coherencia a todo el sitio. Compruebe la lista de [asuntos abiertos](https://github.com/dotnet/docs/issues?q=is%3Aissue+is%3Aopen+label%3Aguidelines-adherence) de los que estamos realizando un seguimiento con vistas a ese objetivo.

## <a name="building-the-docs"></a>Creación de los documentos

La documentación se escribe en [GitHub Flavored Markdown](https://help.github.com/categories/writing-on-github/) y se crea mediante [DocFX](https://dotnet.github.io/docfx/) y otras herramientas internas de publicación o creación. Se hospeda en [docs.microsoft.com](https://docs.microsoft.com/dotnet).

Si desea crear los documentos de forma local, deberá instalar [DocFX](https://dotnet.github.io/docfx/); se recomienda usar las versiones más recientes.

Hay varias formas de utilizar DocFX, y la mayoría de ellas se abordan en la [guía de introducción de DocFX](https://dotnet.github.io/docfx/tutorial/docfx_getting_started.html).
Las instrucciones siguientes usan la versión [basada en la línea de comandos](https://dotnet.github.io/docfx/tutorial/docfx_getting_started.html#2-use-docfx-as-a-command-line-tool) de la herramienta.
Si está familiarizado con otras formas enumeradas en el vínculo anterior, puede usarlas.

**Nota:** Actualmente, DocFX requiere .NET Framework en Windows o Mono (para Linux o macOS). Nuestra intención es portarlo a .NET Core en el futuro.

Con un servidor web integrado, puede crear y obtener una vista previa local del sitio resultante. Vaya a la carpeta core-docs en su equipo y escriba el comando siguiente:

```
docfx -t default --serve
```

Esto inicia la vista previa local en [localhost:8080](http://localhost:8080). A continuación, para ver los cambios, vaya a `http://localhost:8080/[path]`, por ejemplo http://localhost:8080/articles/welcome.html.

**Nota:** Actualmente, la vista previa local no contiene temas, por lo que la apariencia y el comportamiento no serán los mismos que en el sitio de documentación. Estamos trabajando para mejorar esta experiencia.

# <a name="contributing-to-samples"></a>Contribución a los ejemplos

Por ahora, incluya en el artículo el código de ejemplo requerido como bloques de código alineado. El repositorio tiene una carpeta codesnippets, pero no es posible realizar contribuciones públicas.
