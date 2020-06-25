---
title: Editor de código XAML
ms.date: 06/16/2020
ms.topic: conceptual
monikerRange: vs-2019
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: d789ac099e6d0bba7a44f0d6efd7a19beec54c19
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/23/2020
ms.locfileid: "85289935"
---
# <a name="xaml-code-editor"></a>Editor de código XAML

El editor de código XAML del [IDE de Visual Studio](../get-started/visual-studio-ide.md) incluye todas las herramientas que necesita para crear aplicaciones de WPF y UWP para la plataforma Windows y para [Xamarin. Forms](/xamarin/xamarin-forms/user-interface/text/editor/). En este artículo se describe el rol que reproduce el editor de código cuando se desarrollan aplicaciones basadas en XAML y las características que son exclusivas del editor de código XAML en Visual Studio 2019.

Para empezar, echemos un vistazo al IDE (entorno de desarrollo integrado) con un proyecto de WPF abierto. En la imagen siguiente se muestran algunas de las herramientas de IDE clave que se van a usar junto con el editor de código XAML.

:::image type="content" source="media/xaml-code-editor-overview-sml.png" alt-text="El IDE de Visual Studio 2019 con un proyecto de WPF abierto en XAML" lightbox="media/xaml-code-editor-overview-lrg.png":::

Desde la parte inferior izquierda de la imagen en sentido de las agujas del reloj, las herramientas clave del IDE son las siguientes:

- La ventana del **[Editor de código XAML](#xaml-code-editor-ui)** &mdash; es el asunto de este artículo &mdash; en el que se crea y edita el código.
- La ventana **[Diseñador XAML](creating-a-ui-by-using-xaml-designer-in-visual-studio.md)** , donde se diseña la interfaz de usuario.
- La ventana acoplable del **[cuadro de herramientas](../ide/reference/toolbox.md)** , donde se agregan controles a la interfaz de usuario.
- El botón **[depurar](../debugger/debugger-feature-tour.md)** , donde se ejecuta el código y se depura. <br>(También puede editar el código en tiempo real mientras realiza la depuración con la [recarga activa de XAML](xaml-hot-reload.md)).
- La ventana **[Explorador de soluciones](../ide/solutions-and-projects-in-visual-studio.md)** , donde se administran los archivos, proyectos y soluciones.
- La ventana **[propiedades](../ide/reference/properties-window.md)** , donde se cambia la apariencia de la interfaz de usuario y el funcionamiento de los controles de IU.

Para continuar, vamos a obtener más información sobre el editor de código XAML.

## <a name="xaml-code-editor-ui"></a>Interfaz de usuario del editor de código XAML

Mientras que la ventana del editor de código para aplicaciones XAML comparte algunos elementos de interfaz de usuario (IU) que también aparecen en nuestro IDE estándar, también incluye algunas características únicas que facilitan el desarrollo de aplicaciones XAML.

A continuación se muestra la ventana del editor de código XAML.

![La ventana del editor de código XAML en Visual Studio](media/xaml-code-editor-window.png "Captura de pantalla de la ventana del editor de código XAML en Visual Studio 2019")

A continuación, echemos un vistazo a las funciones de cada uno de los elementos de la interfaz de usuario en el editor de código.

### <a name="first-row"></a>Primera fila

En la primera fila de la parte superior de la ventana de código XAML, a la izquierda, hay una pestaña **diseño** , un botón **intercambiar paneles** , una pestaña **XAML** y un botón **XAML emergente** .

![La primera de las dos filas superiores de la ventana del editor de código XAML en Visual Studio, con el lado izquierdo de la primera fila resaltada](media/xaml-code-editor-top-row-left.png "Captura de pantalla de la primera de las dos filas superiores de la ventana del editor de código XAML en Visual Studio 2019, en la que se resaltan los elementos de la interfaz de usuario de la izquierda")

Así es como funcionan:

- La pestaña **diseño** cambia el foco del editor de código XAML al diseñador XAML.
- El botón **intercambiar paneles** invierte la ubicación del diseñador XAML y el editor de código XAML en el IDE.
- La pestaña **XAML** vuelve a cambiar el foco al editor de código XAML.
- El botón **XAML emergente** crea una ventana del editor de código XAML independiente fuera del IDE.

Continuando a la derecha, hay un botón de **expansión vertical** , un botón de **expansión horizontal** y un botón **contraer paneles** .

![La primera de las dos filas superiores de la ventana del editor de código XAML en Visual Studio, con el lado derecho de la primera fila resaltada](media/xaml-code-editor-top-row-right.png "Captura de pantalla de la primera de las dos filas superiores de la ventana del editor de código XAML en Visual Studio 2019, en la que se resaltan los elementos de la interfaz de usuario de la derecha")

Así es como funcionan:

- El botón de **expansión vertical** cambia la ubicación del diseñador XAML y el editor de código XAML en el IDE de una alineación horizontal a una alineación vertical.
- El botón de **división horizontal** cambia la ubicación del diseñador XAML y el editor de código XAML en el IDE de una alineación vertical a una alineación horizontal.
- El botón **contraer panel** le permite contraer lo que se encuentra en el panel inferior, ya sea el editor de código o el diseñador. (Para restaurar el panel inferior, vuelva a elegir el mismo botón, que ahora se denomina botón **expandir panel** ).

<!-- [!TIP]
> You can run two parallel instances of the XAML code editor concurrently by using both the **Pop Out XAML** button and the **Expand Pane** button.
>
> You might find it useful to have one larger window open that reveals more of your code in context and a smaller pane open that has its focus directly on the code that you're working on. -->

### <a name="second-row"></a>Segunda fila

En la segunda fila de la parte superior de la ventana de código XAML, hay dos listas desplegables de ventana. Sin embargo, si ve la información sobre herramientas de estos elementos de la interfaz de usuario, los identifica como el elemento "Element: window" y "Member: window".

![La segunda de las dos primeras filas de la ventana del editor de código XAML en Visual Studio, donde ambas listas desplegables de la ventana están visibles](media/xaml-code-editor-top-row-windows.png "Captura de pantalla del segundo de las dos filas superiores de la ventana del editor de código XAML en Visual Studio 2019, en la que las dos listas desplegables de ventanas están visibles")

Las listas desplegables de la ventana tienen funciones diferentes, como se indica a continuación:

- La **ventana elemento:** de la izquierda le ayuda a ver y navegar a los elementos primarios o relacionados.

  En concreto, se muestra una vista similar a un esquema que revela la estructura de etiqueta del código. Al seleccionar en la lista, el foco en el editor de código se ajustará a la línea de código que incluye el elemento que ha seleccionado.

    ![La lista desplegable elemento: ventana en Visual Studio](media/xaml-element-window-dropdown.png "Captura de pantalla del elemento: lista desplegable de la ventana en Visual Studio 2019")

- La **ventana miembro:** de la derecha ayuda a ver y navegar a los atributos o elementos secundarios.

    En concreto, se muestra una lista de las propiedades del código. Al seleccionar en la lista, el foco en el editor de código se ajustará a la línea de código que incluye la propiedad seleccionada.

    ![La lista desplegable miembro: ventana en Visual Studio](media/xaml-member-window-dropdown.png "Captura de pantalla de la lista desplegable miembro: de la ventana de Visual Studio 2019")

### <a name="middle-pane-code-editor"></a>Panel central, editor de código

El panel central es la parte "Code" del editor de código XAML. Incluye la mayoría de las características que encontrará en el editor de [código IDE](../get-started/tutorial-editor.md). Nos pondremos en contacto con algunas de las características del IDE universal que pueden ayudarle a desarrollar el código XAML. También resaltaremos las características de único a XAML en el IDE.

![El editor de código XAML, el panel central solo, en Visual Studio](media/xaml-code-editor-middle.png "Captura de pantalla del editor de código XAML, solo en el panel central, en Visual Studio 2019")

#### <a name="quick-actions"></a>Acciones rápidas

Puede usar [acciones rápidas](../ide/quick-actions.md) para refactorizar, generar o modificar código de otra forma con una sola acción.

Por ejemplo, una tarea útil que se puede realizar mediante acciones rápidas es quitar las **utilizaciones innecesarias** del código de C# en la pestaña **MainWindow.Xaml.CS** .

A continuación, se indica cómo puede hacerlo.

1. Mantenga el puntero sobre una instrucción using, elija el icono de bombilla y, a continuación, elija **Quitar instrucciones Using innecesarias** en la lista desplegable.

    ![La opción "quitar uso innecesario" del editor IDE del menú acciones rápidas](media/xaml-code-editor-remove-usings.png "Captura de pantalla de la opción quitar innecesariamente del editor del IDE del menú acciones rápidas")

1. Elija si desea corregir todas las repeticiones del **documento**, el **proyecto**o la **solución**.
1. Vea el cuadro de diálogo **vista previa** y, a continuación, elija **aplicar**.

También puede tener acceso a esta característica desde la barra de menús. Para ello, elija **Editar**  >  **IntelliSense**  >  **quitar y ordenar mediante**.

Para obtener más información acerca de cómo usar la configuración, vea la página [ordenar](../ide/reference/sort-usings.md) opciones. Para obtener más información sobre IntelliSense, vea la página [IntelliSense en Visual Studio](../ide/using-intellisense.md) . Y, para obtener más información acerca de algunas de las formas típicas en que los desarrolladores utilizan acciones rápidas, consulte la página [acciones rápidas comunes](../ide/common-quick-actions.md) .

#### <a name="change-tracking"></a>Seguimiento de cambios

El color del margen izquierdo le permite realizar un seguimiento de los cambios realizados en un archivo. Aquí se muestra cómo se relacionan los colores con las acciones que realiza:

- Los cambios realizados desde que se abrió el archivo pero no se guardan se indican con una barra **amarilla** en el margen izquierdo (conocido como el margen de selección).

    ![Editor de código editar con barra amarilla](media/code-editor-edit-yellow.png "Captura de pantalla del editor de código con un cambio marcado con una barra amarilla en el margen de selección.")

- Después de haber guardado los cambios (pero antes de cerrar el archivo), la barra se vuelve **verde**.

    ![Editor de código editar con barra verde](media/code-editor-edit-green.png "Captura de pantalla del editor de código con un cambio marcado con una barra verde en el margen de selección.")

Para activar o desactivar esta característica, cambie la opción **Seguimiento de cambios** en la configuración del **Editor de texto** (**Herramientas** > **Opciones** > **Editor de texto**).

Para obtener más información sobre el seguimiento de cambios &mdash; para incluir las líneas onduladas (también conocidas como "líneas de subrayado") que aparecen en cadenas de código, &mdash; vea la sección **[características del editor](../ide/writing-code-in-the-code-and-text-editor.md#editor-features)** de las [características de la página del editor de código de Visual Studio](../ide/writing-code-in-the-code-and-text-editor.md) .

#### <a name="right-click-context-menu"></a>Hacer clic con el botón secundario en el menú contextual

Al editar el código en el editor de código XAML, hay varias características a las que puede tener acceso mediante el menú contextual. La mayoría de estas características están disponibles universalmente en el IDE de Visual Studio, mientras que otras son específicas del uso de un editor de código junto con una ventana de diseño.

![Menú contextual del editor de código XAML en Visual Studio](media/xaml-code-editor-right-click-menu.png "Captura de pantalla del menú contextual del editor de código XAML en Visual Studio 2019")

Esto es lo que hace cada característica y cómo es útil:

- **Ver código** : abre la ventana de código del lenguaje de programación, que normalmente se muestra junto a la vista predeterminada que incluye la ventana de diseño y el editor de código XAML.
- **Diseñador de vistas** : abre la vista predeterminada que incluye la ventana de diseño y el editor de código XAML. (Si ya está en la vista predeterminada, no hace nada).
- **Acciones rápidas y refactorizaciones** : refactorizar, generar o modificar código de otra forma con una sola acción. Al mantener el mouse sobre el código, verá un icono de bombilla cuando haya disponible una acción rápida o una refactorización. <br>Vea también: [acciones rápidas](../ide/quick-actions.md) y [refactorizar código](../ide/refactoring-in-visual-studio.md).
- **Cambiar nombre...** -Solo cambia el nombre de los espacios de nombres. Si no tiene un espacio de nombres para cambiar el nombre, recibirá un mensaje de error que indica "solo se puede cambiar el nombre de los prefijos de espacio de nombres".
- **Quitar y ordenar espacios de nombres** : quita los espacios de nombres no usados y, a continuación, ordena los espacios de nombres que quedan.
- **Definición de PEEK** : muestra una vista previa de la definición de un tipo sin tener su ubicación actual en el editor. <br>Vea también: ver la [definición](../ide/go-to-and-peek-definition.md#peek-definition) y [ver y editar código mediante el uso de la definición de PEEK](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md).
- **Ir a definición** : navega al origen de un tipo o miembro y abre el resultado en una nueva pestaña. <br>Vea también: [ir a definición](../ide/go-to-and-peek-definition.md#go-to-definition).
- **Envolver con...** -Usar fragmentos de código envolventes, que se agregan alrededor de un bloque de código seleccionado. <br>Vea también: [fragmentos de código de expansión y fragmentos de código envolventes](../ide/code-snippets.md#expansion-snippets-and-surround-with-snippets).
- **Insertar fragmento** de código: inserta un fragmento de código en la ubicación del cursor.
- Fácil de **cortar**
- **Copia** automática
- **Pegado** autoexplicativo
- **Esquematización** : expandir y contraer secciones de código. <br>Vea también: [esquematización](../ide/outlining.md).
- **Control de código fuente** : permite ver el historial de las contribuciones de código a un repositorio de código abierto.

### <a name="middle-pane-scroll-bar"></a>Panel central, barra de desplazamiento

La barra de desplazamiento puede hacer más que desplazarse por el código. También puede utilizarlo para abrir otro panel del editor de código. Además, puede usar la barra de desplazamiento para ayudarle a codificar de forma más eficaz mediante la adición de anotaciones o mediante diferentes modos de presentación.

#### <a name="split-the-code-window"></a>División de la ventana de código

En la barra de desplazamiento del editor de código, hay un botón de **expansión** en la parte superior derecha. Al elegirlo, puede abrir otro panel del editor de código. Esto resulta útil porque funcionan de forma independiente entre sí, por lo que puede usarlos para trabajar en código en diferentes ubicaciones.

![El editor de código XAML, el panel central solo, en Visual Studio](media/code-editor-split-window-button.png "Captura de pantalla del editor de código XAML, solo en el panel central, en Visual Studio 2019")

Para obtener más información sobre cómo dividir una ventana del editor, vea la página [administrar ventanas del editor](../ide/how-to-manage-editor-windows.md) .

#### <a name="use-annotations-or-map-mode"></a>Usar anotaciones o el modo de mapa

También puede cambiar la apariencia de la barra de desplazamiento y las características adicionales que contiene. Por ejemplo, muchas personas desean incluir *anotaciones* en la barra de desplazamiento, que proporcionan indicaciones visuales como cambios de código, puntos de interrupción, marcadores, errores y la posición del símbolo de intercalación.

Otros usuarios aprecian el uso del *modo de mapa*, que muestra líneas de código en miniatura en la barra de desplazamiento. Los desarrolladores que tienen una gran cantidad de código en un archivo pueden encontrar que el modo de asignación realiza un seguimiento de las líneas de código de forma más eficaz que la barra de desplazamiento predeterminada.

Para obtener más información sobre cómo cambiar la configuración predeterminada de la barra de desplazamiento, vea la página [personalizar la barra de desplazamiento](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md) .

## <a name="xaml-specific-features"></a>Características específicas de XAML

La mayoría de las características siguientes están disponibles universalmente en el IDE de Visual Studio, pero se han agregado dimensiones a algunas de ellas que facilitan la codificación de los desarrolladores de XAML.

### <a name="xaml-code-snippets"></a>Fragmentos de código XAML

Los fragmentos de código son pequeños bloques de código reutilizable que puede insertar en un archivo de código mediante el comando del menú contextual **Insertar fragmento** de código o una combinación de métodos abreviados de teclado (**Ctrl** + **K**, **Ctrl** + **X**). Hemos mejorado [IntelliSense](../ide/using-intellisense.md) para que admita la visualización de fragmentos de código XAML, que funcionan tanto para fragmentos de código integrados como para los fragmentos de código personalizados que se agregan manualmente. Algunos fragmentos de código XAML predeterminados son `#region` , `Column definition` , `Row definition` , `Setter` y `Tag` .

![El editor de código XAML con opciones de #region que se muestran en IntelliSense](media/xaml-code-snippets.png "Captura de pantalla del editor de código XAML con opciones de #region que se muestran en IntelliSense")

Para obtener más información, vea las páginas [fragmentos de código](../ide/code-snippets.md) y fragmentos de [código de C#](../ide/visual-csharp-code-snippets.md) .

### <a name="xaml-region-support"></a>Compatibilidad con #region XAML

A partir de Visual Studio 2015, hemos #region soporte técnico disponible para los desarrolladores de XAML en WPF y UWP y, más recientemente, también en [Xamarin. Forms](/xamarin/xamarin-forms/user-interface/text/editor/). En Visual Studio 2019, seguimos realizando mejoras incrementales en #region soporte técnico. Por ejemplo, en la [versión 16,4](/visualstudio/releases/2019/release-notes-v16.4/) y versiones posteriores, #region opciones se muestran cuando empieza a escribir `<!` .

![El editor de código XAML con opciones de #region que se muestran en IntelliSense](media/code-editor-xaml-region.png "Captura de pantalla del editor de código XAML con opciones de #region que se muestran en IntelliSense")

Puede usar regiones si desea agrupar las secciones del código que también desea expandir o contraer.

```xaml
    <!--#region NameOfRegion-->
    Your code is here
    <!--#endregion-->
```

Para obtener más información sobre las regiones, vea la página [#region (referencia de C#)](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-region/) . Y para obtener más información sobre cómo expandir y contraer secciones de código, vea la página de [esquematización](../ide/outlining.md) .

### <a name="xaml-comments"></a>Comentarios XAML

A menudo, los desarrolladores prefieren documentar el código con comentarios. Puede agregar comentarios al código XAML que se encuentra en la pestaña **MainWindow. Xaml** de las siguientes maneras:

- Escriba `<!--` Before a comment y, después, agregue `-->` después del comentario.
- Escriba `<!` y, a continuación, elija `!--` en la lista de opciones.

  ![En el editor de código XAML, haga clic con el botón derecho en cuadro de diálogo Agregar comentarios](media/xaml-code-editor-comments.png "Captura de pantalla del menú contextual para agregar comentarios en el editor de código XAML")

- Seleccione el código que desea rodear con un comentario y, a continuación, elija el botón de **Comentario** en la barra de herramientas del IDE. Para invertir la acción, elija el botón **quitar comentario** .

  ![El botón comentario y el botón Quitar comentario de la barra de herramientas del IDE](media/comment-undo-comment-buttons.png "Captura de pantalla del botón de comentario y del botón Quitar comentario en la barra de herramientas del IDE")

- Seleccione el código que desea rodear con un comentario y, a continuación, presione **Ctrl** + **K**, **Ctrl** + **C**. Para quitar el comentario del código seleccionado, presione **Ctrl** + **K**, **Ctrl** + **U**.

Para obtener más información sobre cómo usar los comentarios en el código de C# que se encuentra en la pestaña **MainWindow.Xaml.CS** , vea la página [comentarios de documentación](/dotnet/csharp/language-reference/language-specification/documentation-comments/) .

### <a name="xaml-lightbulbs"></a>Bombillas de XAML

Los iconos de bombilla que aparecen en el código XAML forman parte de las [acciones rápidas](../ide/quick-actions.md) que puede usar para refactorizar, generar o modificar el código de otra manera.

Estos son algunos ejemplos de cómo pueden beneficiarse de la experiencia de codificación XAML:

- **Quite los espacios de nombres innecesarios**. En el editor de código XAML, los espacios de nombres innecesarios aparecen en texto atenuado. Si mantiene el cursor sobre un uso innecesario, aparecerá una bombilla. Cuando elija la opción **Quitar espacios de nombres innecesarios** de la lista desplegable, verá una vista previa de la que puede quitar.

  ![La opción Quitar espacios de nombres innecesarios del editor de código XAML de la bombilla de acciones rápidas](media/xaml-code-editor-dimmed-namespaces-preview.png "Captura de pantalla de la opción Quitar espacios de nombres innecesarios del editor de código XAML que aparece con las acciones rápidas bombillas")

- **Cambiar el nombre del espacio de nombres**. Esta característica, que está disponible en el menú contextual después de resaltar un espacio de nombres, facilita el cambio de varias instancias de una configuración al mismo tiempo. También puede tener acceso a esta característica mediante la barra de menús, **Editar**  >  **refactorizar**  >  **cambio de nombre**o presionando **Ctrl** + **r**y, a continuación, **Ctrl** + **r** de nuevo.

  ![La opción de espacio de nombres Rename del editor de código XAML del menú contextual de clic con el botón secundario](media/code-editor-rename-namespace.png "Captura de pantalla de la opción de espacio de nombres Rename del editor de código XAML que aparece al hacer clic con el botón derecho en el menú contextual")

  Para obtener más información, consulte la página de [refactorización cambiar el nombre de un símbolo de código](../ide/reference/rename.md) .

### <a name="conditional-xaml-for-uwp"></a>Código XAML condicional para UWP

El XAML condicional ofrece una manera de usar el método [ApiInformation.IsApiContractPresent](/uwp/api/windows.foundation.metadata.apiinformation.isapicontractpresent/) en el marcado XAML. Esto te permite establecer las propiedades y crear instancias de objetos en el marcado en función de la presencia de una API, sin tener que usar código subyacente.

Para obtener más información, vea la página [XAML condicional](/windows/uwp/debug-test-perf/conditional-xaml/) y la página [hospedar controles XAML de UWP en aplicaciones de escritorio (Islas XAML)](/windows/apps/desktop/modernize/xaml-islands/) .

### <a name="xaml-structure-visualizer"></a>Visualizador de estructura XAML

La característica visualizador de estructura en el editor de código muestra líneas guía de estructura, que son líneas discontinuas verticales que indican elementos de etiqueta abiertos y cerrados coincidentes en el código. Estas líneas verticales facilitan la visualización de dónde comienzan y terminan los bloques lógicos.

Para obtener más información, vea la página de [código navegar](../ide/navigating-code.md) .

### <a name="intellicode-for-xaml"></a>IntelliCode para XAML

Cuando se agrega una etiqueta XAML al código, normalmente se empieza con un corchete angular de apertura `<` . Cuando escribe el corchete angular, aparece un menú IntelliCode que enumera algunas de las etiquetas XAML más populares. Elija el que desee agregar rápidamente al código.

Puede reconocer las selecciones de IntelliCode porque aparecen en la parte superior de la lista y son destacan.

![La lista IntelliCode para el editor de texto XAML](media/xaml-intellicode-selection.png "Captura de pantalla de la lista IntelliCode para el editor de texto XAML")

Para obtener más información, consulte la página [de información general de IntelliCode](/visualstudio/intellicode/overview/) .

### <a name="settings"></a>Configuración

Para obtener más información sobre *todos* los valores del IDE de Visual Studio, vea las [características de la página del editor de código](../ide/writing-code-in-the-code-and-text-editor.md) .

## <a name="xaml-optional-settings"></a>Configuración opcional de XAML

Puede usar el cuadro de diálogo [Opciones](../ide/reference/options-dialog-box-visual-studio.md) para cambiar la configuración predeterminada para el editor de código XAML. Para ver la configuración, elija **herramientas**  >  **Opciones**  >  **Editor de texto**  >  **XAML**.

![La lista de opciones para el editor de texto XAML](media/xaml-tools-options.png "Captura de pantalla de la lista de opciones para el editor de texto XAML")

> [!NOTE]
> También puede usar métodos abreviados de teclado para tener acceso al cuadro de diálogo Opciones. Aquí se muestra cómo: Presione **Ctrl** + **Q** para buscar en el IDE, escriba **Opciones**y, a continuación, presione **entrar**. A continuación, presione **Ctrl** + **E** para buscar en el cuadro de diálogo Opciones, escriba **Editor de texto**, presione **entrar**, escriba **XAML**y, a continuación, presione **entrar**.
>  
> Para obtener más información sobre los métodos abreviados de teclado, vea la página [sugerencias de acceso directo para Visual Studio](../ide/productivity-shortcuts.md#code-editor) .

### <a name="universal-text-editor-options"></a>Opciones del editor de texto universal

En el cuadro de diálogo [Opciones](../ide/reference/options-text-editor-xaml-formatting.md) de XAML, los tres primeros elementos siguientes son universales para todos los lenguajes de programación que admite el IDE de Visual Studio. Visite la información vinculada en la tabla siguiente para obtener más información acerca de estas opciones y cómo usarlas.

|Nombre  |Más información  |
|---------|---------|
|General  | [Cuadro de diálogo Opciones: editor de texto > todos los lenguajes](../ide/reference/options-text-editor-all-languages.md) |
|Barras de desplazamiento | [Opciones, Editor de texto, Todos los idiomas, Barras de desplazamiento](../ide/reference/options-text-editor-all-languages-scroll-bars.md) |
|Tabulaciones  |  [Opciones, editor de texto, todos los lenguajes, pestañas](../ide/reference/options-text-editor-all-languages-tabs.md) |

### <a name="xaml-specific-text-editor-options"></a>Opciones del editor de texto específico de XAML

En la tabla siguiente se enumeran los valores del cuadro de diálogo [Opciones](../ide/reference/options-text-editor-xaml-formatting.md) que pueden mejorar la experiencia de edición al desarrollar aplicaciones basadas en XAML. Visite la información vinculada para obtener más información acerca de estas opciones y cómo usarlas.

|Nombre  |Más información  |
|---------|---------|
|Formato | [Opciones, Editor de texto, XAML, Formato](../ide/reference/options-text-editor-xaml-formatting.md) |
|Varios |  [Opciones, editor de texto, XAML y varios](../ide/reference/options-text-editor-xaml-miscellaneous.md) |

> [!TIP]
> La configuración de **nombre de método de controlador de eventos en mayúsculas** en la sección **varios** es especialmente útil para los desarrolladores de XAML. Esta opción está *desactivada* de forma predeterminada porque es nueva, pero se recomienda establecerla en *activado* para admitir el uso correcto de mayúsculas y minúsculas en el código.

## <a name="next-steps"></a>Pasos siguientes

Para obtener más información sobre cómo editar el código en tiempo real mientras ejecuta la aplicación en modo de depuración, consulte la página de [recarga activa de XAML](xaml-hot-reload.md) .

## <a name="see-also"></a>Vea también

- [Características del editor de código de Visual Studio](../ide/writing-code-in-the-code-and-text-editor.md)
- [XAML en aplicaciones de UWP](/windows/uwp/xaml-platform/xaml-overview/)
- [XAML en aplicaciones de Xamarin.Forms](/xamarin/xamarin-forms/xaml/)
- [Desarrollo de aplicaciones móviles de Xamarin (Mac)](/visualstudio/mac/xamarin/)
- [Visual Studio 2019 para Mac: paseo por IDE (Mac)](/visualstudio/mac/ide-tour/)
