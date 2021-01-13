---
title: Editor de código XAML
description: Un paseo por el editor de código XAML de Visual Studio
ms.date: 06/16/2020
ms.topic: overview
monikerRange: vs-2019
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 29fa854ab00764fc0166a53d8b48989f2c74f036
ms.sourcegitcommit: d526af3642163180e0cc3e1e73b0a00f02542683
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/31/2020
ms.locfileid: "97833304"
---
# <a name="xaml-code-editor"></a>Editor de código XAML

El editor de código XAML del [IDE de Visual Studio](../get-started/visual-studio-ide.md) incluye todas las herramientas que necesita para crear aplicaciones WPF y para UWP para la plataforma Windows y [Xamarin.Forms](/xamarin/xamarin-forms/user-interface/text/editor/). En este artículo se describe el papel que desempeña el editor de código cuando se desarrollan aplicaciones basadas en XAML y las características que son exclusivas del editor de código XAML de Visual Studio 2019.

Para empezar, se examinará el IDE (entorno de desarrollo integrado) con un proyecto de WPF abierto. En la imagen siguiente se muestran algunas de las herramientas clave del IDE que se van a usar junto con el editor de código XAML.

:::image type="content" source="media/xaml-code-editor-overview-sml.png" alt-text="IDE de Visual Studio 2019 con un proyecto de WPF abierto en XAML" lightbox="media/xaml-code-editor-overview-lrg.png":::

Desde la parte inferior izquierda de la imagen en sentido de las agujas del reloj, las herramientas clave del IDE son las siguientes:

- La ventana del **[editor de código de XAML](#xaml-code-editor-ui)** (el tema de este artículo) donde se crea y edita el código.
- La ventana **[Diseñador XAML](creating-a-ui-by-using-xaml-designer-in-visual-studio.md)** , donde se diseña la interfaz de usuario.
- La ventana acoplable **[Cuadro de herramientas](../ide/reference/toolbox.md)** , donde se agregan controles a la interfaz de usuario.
- El botón **[Depurar](../debugger/debugger-feature-tour.md)** , donde se ejecuta el código y se depura. <br>(También puede editar el código en tiempo real mientras realiza la depuración con [Recarga activa de XAML](xaml-hot-reload.md)).
- La ventana **[Explorador de soluciones](../ide/solutions-and-projects-in-visual-studio.md)** , donde se administran los archivos, los proyectos y las soluciones.
- La ventana **[Propiedades](../ide/reference/properties-window.md)** , donde se cambia la apariencia de la interfaz de usuario y el funcionamiento de sus controles.

Para continuar, obtendrá más información sobre el editor de código XAML.

## <a name="xaml-code-editor-ui"></a>Interfaz de usuario del editor de código XAML

Mientras que la ventana del editor de código para aplicaciones XAML comparte algunos elementos de la interfaz de usuario (IU) que también aparecen en el IDE estándar, además incluye algunas características únicas que facilitan el desarrollo de aplicaciones XAML.

A continuación se muestra la propia ventana del editor de código XAML.

![Ventana del editor de código XAML en Visual Studio](media/xaml-code-editor-window.png "Captura de pantalla de la ventana del editor de código XAML en Visual Studio 2019")

Ahora se examinarán las funciones de cada uno de los elementos de la interfaz de usuario en el editor de código.

### <a name="first-row"></a>Primera fila

En la primera fila de la parte superior de la ventana de código XAML, a la izquierda, hay una pestaña **Diseño**, un botón **Intercambiar paneles**, una pestaña **XAML** y un botón **XAML** emergente.

![La primera de las dos filas superiores de la ventana del editor de código XAML en Visual Studio, con el lado izquierdo de la primera fila resaltado](media/xaml-code-editor-top-row-left.png "Captura de pantalla de la primera de las dos filas superiores de la ventana del editor de código XAML en Visual Studio 2019, con los elementos de la interfaz de usuario del lado izquierdo resaltados")

Este es su funcionamiento:

- La pestaña **Diseño** cambia el foco del editor de código XAML al Diseñador XAML.
- El botón **Intercambiar paneles** invierte la ubicación del Diseñador XAML y el editor de código XAML en el IDE.
- La pestaña **XAML** vuelve a cambiar el foco al editor de código XAML.
- El botón emergente **XAML** crea una ventana del editor de código XAML independiente fuera del IDE.

Continuando a la derecha, hay un botón **División vertical**, un botón **División horizontal** y un botón **Contraer panel**.

![La primera de las dos filas superiores de la ventana del editor de código XAML en Visual Studio, con el lado derecho de la primera fila resaltado](media/xaml-code-editor-top-row-right.png "Captura de pantalla de la primera de las dos filas superiores de la ventana del editor de código XAML en Visual Studio 2019, con los elementos de la interfaz de usuario del lado derecho resaltados")

Este es su funcionamiento:

- El botón **División vertical** cambia la ubicación del Diseñador XAML y el editor de código XAML en el IDE de una alineación horizontal a vertical.
- El botón **División horizontal** cambia la ubicación del Diseñador XAML y el editor de código XAML en el IDE de una alineación vertical a horizontal.
- El botón **Contraer panel** permite contraer lo que se encuentra en el panel inferior, ya sea el editor de código o el diseñador. (Para restaurar el panel inferior, vuelva a elegir el mismo botón, que ahora se denomina **Expandir panel**).

<!-- [!TIP]
> You can run two parallel instances of the XAML code editor concurrently by using both the **Pop Out XAML** button and the **Expand Pane** button.
>
> You might find it useful to have one larger window open that reveals more of your code in context and a smaller pane open that has its focus directly on the code that you're working on. -->

### <a name="second-row"></a>Segunda fila

En la segunda fila de la parte superior de la ventana de código XAML, hay dos listas desplegables Ventana. Pero si observa la información sobre herramientas de estos elementos de la interfaz de usuario, los identifica como "Elemento: Ventana" y "Miembro: Ventana".

![La segunda de las dos primeras filas de la ventana del editor de código XAML en Visual Studio, donde se ven las dos listas desplegables Ventana](media/xaml-code-editor-top-row-windows.png "Captura de pantalla de la segunda de las dos filas superiores de la ventana del editor de código XAML en Visual Studio 2019, donde se ven las dos listas desplegables Ventana")

Las listas desplegables Ventana tienen funciones diferentes, como se indica a continuación:

- La lista **Elemento: Ventana** de la izquierda permite ver y navegar a elementos principales o del mismo nivel.

  En concreto, se muestra una vista de tipo esquema en la que se revela la estructura de etiquetas del código. Al seleccionar en la lista, el foco en el editor de código se ajustará a la línea de código en la que se incluya el elemento que ha seleccionado.

    ![Lista desplegable Elemento: Ventana en Visual Studio](media/xaml-element-window-dropdown.png "Captura de pantalla de la lista desplegable Elemento: Ventana en Visual Studio 2019")

- La lista **Miembro: Ventana** de la derecha permite ver y navegar a atributos o elementos secundarios.

    En concreto, muestra una lista de las propiedades del código. Al seleccionar en la lista, el foco en el editor de código se ajustará a la línea de código en la que se incluya la propiedad que ha seleccionado.

    ![La lista desplegable Miembro: Ventana en Visual Studio](media/xaml-member-window-dropdown.png "Captura de pantalla de la lista desplegable Miembro: Ventana en Visual Studio 2019")

### <a name="middle-pane-code-editor"></a>Panel central, editor de código

El panel central es la parte de "código" del editor de código XAML. Incluye la mayoría de las características que encontrará en el [editor de código del IDE](../get-started/tutorial-editor.md). Se describirán algunas de las características del IDE universal que pueden ayudarle a desarrollar el código XAML. También se resaltarán las características únicas de XAML en el IDE.

![Editor de código XAML, solo el panel central, en Visual Studio](media/xaml-code-editor-middle.png "Captura de pantalla del editor de código XAML, solo el panel central, en Visual Studio 2019")

#### <a name="quick-actions"></a>Acciones rápidas

Puede usar [Acciones rápidas](../ide/quick-actions.md) para refactorizar, generar o modificar el código de otra manera con una sola acción.

Por ejemplo, una tarea útil que puede realizar mediante Acciones rápidas es **Eliminar instrucciones Using innecesarias** del código de C# en la pestaña **MainWindow.xaml.cs**.

A continuación se muestra cómo hacerlo:

1. Mantenga el puntero sobre una instrucción Using, elija el icono de bombilla y, después, seleccione **Eliminar instrucciones Using innecesarias** en la lista desplegable.

    ![La opción "Eliminar instrucciones Using innecesarias" del editor del IDE en el menú Acciones rápidas](media/xaml-code-editor-remove-usings.png "Captura de pantalla de la opción Eliminar instrucciones Using innecesarias del editor del IDE en el menú Acciones rápidas")

1. Elija si quiere corregir todas las repeticiones en el **Documento**, el **Proyecto** o la **Solución**.
1. Vea el cuadro de diálogo **Vista previa** y después elija **Aplicar**.

También puede acceder a esta característica desde la barra de menús. Para ello, elija **Editar** > **IntelliSense** > **Eliminar y ordenar instrucciones Using**.

Para obtener más información sobre la configuración de las instrucciones Using, vea la página [Ordenación de instrucciones Using](../ide/reference/sort-usings.md). Para obtener más información sobre IntelliSense, vea la página [IntelliSense en Visual Studio](../ide/using-intellisense.md). Y, para obtener más información sobre las formas típicas en que los desarrolladores usan Acciones rápidas, vea la página [Acciones rápidas comunes](../ide/common-quick-actions.md).

#### <a name="change-tracking"></a>Seguimiento de cambios

El color del margen izquierdo le permite realizar un seguimiento de los cambios realizados en un archivo. Aquí se muestra la relación de los colores con las acciones que se realizan:

- Los cambios que haya realizado pero no se hayan guardado desde que se ha abierto el archivo se indican mediante una barra **amarilla** en el margen izquierdo (conocido como margen de selección).

    ![Edición en el editor de código con la barra amarilla](media/code-editor-edit-yellow.png "Captura de pantalla del editor de código con un cambio marcado con una barra amarilla en el margen de selección.")

- Una vez que haya guardado los cambios (pero antes de cerrar el archivo), la barra se volverá de color **verde**.

    ![Edición en el editor de código con la barra verde](media/code-editor-edit-green.png "Captura de pantalla del editor de código con un cambio marcado con una barra verde en el margen de selección.")

Para activar o desactivar esta característica, cambie la opción **Seguimiento de cambios** en la configuración del **Editor de texto** (**Herramientas** > **Opciones** > **Editor de texto**).

Para obtener más información sobre el seguimiento de cambios, e incluir las líneas onduladas (también conocidas como "garabatos") que aparecen bajo las cadenas de código, vea la sección **[Características del editor](../ide/writing-code-in-the-code-and-text-editor.md#editor-features)** de la página [Características del editor de código de Visual Studio](../ide/writing-code-in-the-code-and-text-editor.md).

#### <a name="right-click-context-menu"></a>Clic con el botón derecho en el menú contextual

Al modificar el código en el editor de código XAML, hay varias características a las que se puede acceder mediante el menú contextual. La mayoría de estas características están disponibles de forma universal en el IDE de Visual Studio, mientras que otras son específicas del uso de un editor de código junto con una ventana de diseño.

![Captura de pantalla del menú contextual del editor de código XAML en Visual Studio 2019.](media/xaml-code-editor-right-click-menu.png)

Esto es lo que hace cada característica y su utilidad:

- **Ver código**: abre la ventana de código del lenguaje de programación, que normalmente se muestra junto a la vista predeterminada que incluye la ventana Diseño y el editor de código XAML.
- **Diseñador de vistas**: abre la vista predeterminada que incluye la ventana Diseño y el editor de código XAML. (Si ya está en la vista predeterminada, no hace nada).
- **Acciones rápidas y refactorizaciones**: permite refactorizar, generar o modificar el código con una sola acción. Al mantener el mouse sobre el código, verá un icono de bombilla cuando haya disponible una acción rápida o una refactorización. <br>Vea también: [Acciones rápidas](../ide/quick-actions.md) y [Refactorización del código](../ide/refactoring-in-visual-studio.md).
- **Cambiar nombre...** : solo cambia el nombre de los espacios de nombres. Si no tiene un espacio de nombres para cambiar el nombre, recibirá un mensaje de error que indica "Solo se puede cambiar el nombre de los prefijos de espacio de nombres".
- **Quitar y ordenar espacios de nombres**: quita los espacios de nombres sin usar y, después, ordena los que queden.
- **Ver la definición**: obtiene una vista previa de la definición de un tipo sin abandonar la ubicación actual en el editor. <br>Vea también: [Ver la definición](../ide/go-to-and-peek-definition.md#peek-definition) y [Visualización y edición de código mediante Ver la definición](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md).
- **Ir a definición**: se desplaza hasta el origen de un tipo o miembro, y abre el resultado en una pestaña nueva. <br>Vea también: [Ir a definición](../ide/go-to-and-peek-definition.md#go-to-definition).
- **Rodear con...** : permite usar fragmentos de código envolventes, que se agregan alrededor de un bloque de código seleccionado. <br>Vea también: [Fragmentos de código de expansión y fragmentos de código Rodear con](../ide/code-snippets.md#expansion-snippets-and-surround-with-snippets).
- **Insertar fragmento de código**: inserta un fragmento de código en la ubicación del cursor.
- **Cortar**: no necesita explicación.
- **Copiar**: no necesita explicación.
- **Pegar**: no necesita explicación.
- **Esquematización**: sirve para expandir y contraer secciones de código. <br>Vea también: [Esquematización](../ide/outlining.md).
- **Control de código fuente**: permite ver el historial de las contribuciones de código a un repositorio de código abierto.

### <a name="middle-pane-scroll-bar"></a>Panel central, barra de desplazamiento

La barra de desplazamiento puede hacer más que desplazarse por el código. También se puede usar para abrir otro panel del editor de código. Además, puede utilizar la barra de desplazamiento como ayuda para codificar de forma más eficaz mediante la adición de anotaciones o el uso de otros modos de presentación.

#### <a name="split-the-code-window"></a>División de la ventana de código

En la barra de desplazamiento del editor de código, hay un botón **Dividir** en la parte superior derecha. Al elegirlo, puede abrir otro panel del editor de código. Esto resulta útil porque funcionan de forma independiente, por lo que puede usarlos para trabajar en código en diferentes ubicaciones.

![Captura de pantalla en la que se muestra el panel central del editor de código XAML en Visual Studio 2019 con el botón de vista en dos paneles resaltado en la parte superior derecha del panel.](media/code-editor-split-window-button.png)

Para obtener más información sobre cómo dividir una ventana del editor, vea la página [Administración de ventanas del editor](../ide/how-to-manage-editor-windows.md).

#### <a name="use-annotations-or-map-mode"></a>Uso de anotaciones o el modo de mapa

También puede cambiar la apariencia de la barra de desplazamiento y las características adicionales que contiene. Por ejemplo, a muchos usuarios les gusta incluir *anotaciones* en la barra de desplazamiento, que proporcionan indicaciones visuales como cambios de código, puntos de interrupción, marcadores, errores y la posición del símbolo de inserción.

Otros prefieren usar el *modo de mapa*, que muestra líneas de código en miniatura en la barra de desplazamiento. Es posible que los desarrolladores que tienen gran cantidad de código en un archivo comprueben que el modo de mapa realiza un seguimiento más eficaz de las líneas de código que la barra de desplazamiento predeterminada.

Para obtener más información sobre cómo cambiar la configuración predeterminada de la barra de desplazamiento, vea la página [Personalización de la barra de desplazamiento](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md).

## <a name="xaml-specific-features"></a>Características específicas de XAML

La mayoría de las características siguientes están disponibles de manera universal en el IDE de Visual Studio, pero se han agregado dimensiones a algunas de ellas que facilitan la programación para los desarrolladores de XAML.

### <a name="xaml-code-snippets"></a>Fragmentos de código de XAML

Los fragmentos de código son pequeños bloques de código reutilizable que se pueden insertar en un archivo de código mediante el comando del menú contextual **Insertar fragmento de código**, o bien una combinación de métodos abreviados de teclado (**Ctrl**+**K**, **Ctrl**+**X**). Se ha mejorado [IntelliSense](../ide/using-intellisense.md) para admitir la visualización de fragmentos de código XAML, lo que funciona tanto en fragmentos de código integrados como en los fragmentos de código personalizados que agregue de forma manual. Algunos fragmentos de código XAML predeterminados son `#region`, `Column definition`, `Row definition`, `Setter` y `Tag`.

![Editor de código XAML con opciones de fragmentos de código XAML que se muestran en IntelliSense](media/xaml-code-snippets.png "Captura de pantalla del editor de código XAML con opciones de fragmentos de código XAML que se muestran en IntelliSense")

Para obtener más información, vea las páginas [Fragmentos de código](../ide/code-snippets.md) y [Fragmentos de código de C#](../ide/visual-csharp-code-snippets.md).

### <a name="xaml-region-support"></a>Compatibilidad con #region de XAML

A partir de Visual Studio 2015, la compatibilidad con #region se puso a disposición de los desarrolladores de XAML en WPF y UWP, y más recientemente, también en [Xamarin.Forms](/xamarin/xamarin-forms/user-interface/text/editor/). En Visual Studio 2019, se siguen realizando mejoras incrementales para admitir #region. Por ejemplo, en la [versión 16.4](/visualstudio/releases/2019/release-notes-v16.4/) y posteriores, las opciones de #region se muestran cuando comienza a escribir `<!`.

![Editor de código XAML con opciones de #region que se muestran en IntelliSense](media/code-editor-xaml-region.png "Captura de pantalla del editor de código XAML con las opciones de #region que se muestran en IntelliSense")

Puede usar las regiones si quiere agrupar las secciones del código que también quiere expandir o contraer.

```xaml
    <!--#region NameOfRegion-->
    Your code is here
    <!--#endregion-->
```

Para obtener más información sobre las regiones, vea la página [#region (referencia de C#)](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-region/). Y para obtener más información sobre cómo expandir y contraer secciones de código, vea la página [Esquematización](../ide/outlining.md).

### <a name="xaml-comments"></a>Comentarios de XAML

A menudo, los desarrolladores prefieren documentar el código mediante comentarios. Puede agregar comentarios al código XAML que se encuentra en la pestaña **MainWindow.xaml** de las siguientes maneras:

- Escriba `<!--` antes de un comentario y, luego, agregue `-->` después del comentario.
- Escriba `<!` y, luego, elija `!--` en la lista de opciones.

  ![Cuadro de diálogo Agregar comentarios del menú contextual del editor de código XAML](media/xaml-code-editor-comments.png "Captura de pantalla del menú contextual para agregar comentarios en el editor de código XAML")

- Seleccione el código que quiera rodear con un comentario y, después, elija el botón **Comentario** de la barra de herramientas del IDE. Para invertir la acción, elija el botón **Quitar marca de comentario**.

  ![Los botones Comentario y Quitar marca de comentario de la barra de herramientas del IDE](media/comment-undo-comment-buttons.png "Captura de pantalla de los botones Comentario y Quitar marca de comentario de la barra de herramientas del IDE")

- Seleccione el código que quiera rodear con un comentario y, después, presione **Ctrl**+**K**, **Ctrl**+**C**. Para quitar el comentario del código seleccionado, presione **Ctrl**+**K**, **Ctrl**+**U**.

Para obtener más información sobre cómo usar los comentarios en el código de C# que se encuentra en la pestaña **MainWindow.xaml.cs**, vea la página [Comentarios de documentación](/dotnet/csharp/language-reference/language-specification/documentation-comments/).

### <a name="xaml-lightbulbs"></a>Bombillas de XAML

Los iconos de bombilla que aparecen en el código XAML forman parte de las [Acciones rápidas](../ide/quick-actions.md) que puede usar para refactorizar, generar o modificar el código.

Estos son algunos ejemplos de cómo puede mejorar la experiencia de programación de XAML:

- **Quitar espacios de nombres no necesarios**. En el editor de código XAML, los espacios de nombres innecesarios aparecen en texto atenuado. Si mantiene el cursor sobre un uso innecesario, aparecerá una bombilla. Al elegir la opción **Quitar espacios de nombres innecesarios** de la lista desplegable, verá una vista previa de los que puede quitar.

  ![Opción Quitar espacios de nombres innecesarios del editor de código XAML de la bombilla de Acciones rápidas](media/xaml-code-editor-dimmed-namespaces-preview.png "Captura de pantalla de la opción Quitar espacios de nombres innecesarios del editor de código XAML que aparece al usar la bombilla de Acciones rápidas")

- **Cambiar el nombre del espacio de nombres**. Esta característica, que está disponible en el menú contextual después de resaltar un espacio de nombres, facilita el cambio de varias instancias de un valor al mismo tiempo. También puede acceder a esta característica mediante la barra de menús, **Editar** > **Refactorizar** > **Cambiar nombre**, o bien si presiona **Ctrl**+**R** y después **Ctrl**+**R** de nuevo.

  ![Opción Cambiar el nombre del espacio de nombres del editor de código XAML del menú contextual](media/code-editor-rename-namespace.png "Captura de pantalla de la opción Cambiar el nombre del espacio de nombres del editor de código XAML que aparece al usar el menú contextual")

  Para obtener más información, vea la página [Refactorización de cambio de nombre de un símbolo de código](../ide/reference/rename.md).

### <a name="conditional-xaml-for-uwp"></a>Código XAML condicional para UWP

El XAML condicional ofrece una manera de usar el método [ApiInformation.IsApiContractPresent](/uwp/api/windows.foundation.metadata.apiinformation.isapicontractpresent/) en el marcado XAML. Esto te permite establecer las propiedades y crear instancias de objetos en el marcado en función de la presencia de una API, sin tener que usar código subyacente.

Para obtener más información, vea las páginas [XAML condicional](/windows/uwp/debug-test-perf/conditional-xaml/) y [Hospedaje de controles XAML para UWP en aplicaciones de escritorio (islas XAML)](/windows/apps/desktop/modernize/xaml-islands/).

### <a name="xaml-structure-visualizer"></a>Visualizador de estructura de XAML

La característica Visualizador de estructura del editor de código muestra líneas guía de estructura, que son líneas discontinuas verticales que indican los elementos de etiqueta de apertura y cierre coincidentes en el código. Estas líneas verticales facilitan ver dónde empiezan y acaban los bloques lógicos.

Para obtener más información, vea la página [Navegación por el código](../ide/navigating-code.md).

### <a name="intellicode-for-xaml"></a>IntelliCode para lenguaje XAML

Cuando se agrega una etiqueta XAML al código, normalmente se empieza con un corchete angular de apertura `<`. Al escribir ese corchete angular, aparece un menú de IntelliCode en el que se enumeran algunas de las etiquetas XAML más populares. Elija la que quiera agregar rápidamente al código.

Puede reconocer las selecciones de IntelliCode porque aparecen en la parte superior de la lista y tienen estrellas.

![Lista de IntelliCode para el editor de texto XAML](media/xaml-intellicode-selection.png "Captura de pantalla de la lista de IntelliCode para el editor de texto XAML")

Para obtener más información, vea la página [Introducción a IntelliCode](/visualstudio/intellicode/overview/).

### <a name="settings"></a>Configuración

Para obtener más información sobre *todos* los valores del IDE de Visual Studio, vea la página [Características del editor de código](../ide/writing-code-in-the-code-and-text-editor.md).

## <a name="xaml-optional-settings"></a>Valores opcionales de XAML

Puede usar el cuadro de diálogo [Opciones](../ide/reference/options-dialog-box-visual-studio.md) para cambiar los valores predeterminados del editor de código de XAML. Para ver los valores, elija **Herramientas** > **Opciones** > **Editor de texto** > **XAML**.

![Lista Opciones para el editor de texto XAML](media/xaml-tools-options.png "Captura de pantalla de la lista Opciones para el editor de texto XAML")

> [!NOTE]
> También puede usar métodos abreviados de teclado para acceder al cuadro de diálogo Opciones. Esta es la manera de hacerlo: Presione **Ctrl**+**Q** para buscar en el IDE, escriba **Opciones** y, después, presione **Entrar**. A continuación, presione **Ctrl**+**E** para buscar en el cuadro de diálogo Opciones, escriba **Editor de texto**, presione **Entrar**, escriba **XAML** y, después, presione **Entrar**.
>  
> Para obtener más información sobre los métodos abreviados de teclado, vea [Sugerencias de accesos directos para Visual Studio](../ide/productivity-shortcuts.md#code-editor).

### <a name="universal-text-editor-options"></a>Opciones universales del editor de texto

En el cuadro de diálogo [Opciones](../ide/reference/options-text-editor-xaml-formatting.md) para XAML, los tres primeros elementos siguientes son universales para todos los lenguajes de programación que admite el IDE de Visual Studio. Visite la información con vínculos de la tabla siguiente para obtener más información sobre estas opciones y cómo usarlas.

|Nombre  |Más información  |
|---------|---------|
|General  | [Cuadro de diálogo Opciones: Editor de texto > Todos los lenguajes](../ide/reference/options-text-editor-all-languages.md) |
|Barras de desplazamiento | [Opciones, Editor de texto, Todos los idiomas, Barras de desplazamiento](../ide/reference/options-text-editor-all-languages-scroll-bars.md) |
|Tabulaciones  |  [Opciones, editor de texto, todos los lenguajes, pestañas](../ide/reference/options-text-editor-all-languages-tabs.md) |

### <a name="xaml-specific-text-editor-options"></a>Opciones del editor de texto específicas de XAML

En la tabla siguiente se enumeran los valores del cuadro de diálogo [Opciones](../ide/reference/options-text-editor-xaml-formatting.md) que pueden mejorar la experiencia de edición al desarrollar aplicaciones basadas en XAML. Visite la información con vínculos para obtener más información sobre estas opciones y cómo usarlas.

|Nombre  |Más información  |
|---------|---------|
|Formato | [Opciones, Editor de texto, XAML, Formato](../ide/reference/options-text-editor-xaml-formatting.md) |
|Varios |  [Opciones, editor de texto, XAML y varios](../ide/reference/options-text-editor-xaml-miscellaneous.md) |

> [!TIP]
> La opción **Poner en mayúscula el nombre de método del controlador de eventos** de la sección **Varios** es especialmente útil para los desarrolladores de XAML. Esta opción está *desactivada* de forma predeterminada porque es nueva, pero se recomienda *activarla* para admitir el uso de mayúsculas adecuado en el código.

## <a name="next-steps"></a>Pasos siguientes

Para obtener más información sobre cómo editar el código en tiempo real mientras ejecuta la aplicación en modo de depuración, vea la página [Recarga activa de XAML](xaml-hot-reload.md).

## <a name="see-also"></a>Vea también

- [Características del editor de código de Visual Studio](../ide/writing-code-in-the-code-and-text-editor.md)
- [XAML en aplicaciones de UWP](/windows/uwp/xaml-platform/xaml-overview/)
- [XAML en aplicaciones de Xamarin.Forms](/xamarin/xamarin-forms/xaml/)
- [Desarrollo de aplicaciones móviles de Xamarin (Mac)](/visualstudio/mac/xamarin/)
- [Visual Studio 2019 para Mac: paseo por el IDE (Mac)](/visualstudio/mac/ide-tour/)
