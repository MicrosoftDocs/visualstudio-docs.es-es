---
title: Personalizar los diseños de ventana
description: Aprenda a personalizar las características que Windows exhibe para crear diseños que funcionen mejor con varios flujos de trabajo de desarrollo.
ms.custom: SEO-VS-2020
ms.date: 07/31/2020
ms.topic: conceptual
f1_keywords:
- vs.windows
- vs.environment
helpviewer_keywords:
- windows [Visual Studio], managing
- custom window configurations
- layout [Visual Studio], window management
- document windows [Visual Studio]
- interface modes
- AutoHide windows
- MDI, window interface modes
- multiple monitors
- Tabbed Document mode
- debug mode
- custom layouts
ms.assetid: 7517ff13-76de-4ecf-9c1b-eb9b7ff4d718
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c433a6faf3eab9dd959cc25f26033c74852c0899
ms.sourcegitcommit: 66cda27b63c9b55782b1db223a6dbda9f8cabe13
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2020
ms.locfileid: "95006671"
---
# <a name="customize-window-layouts-in-visual-studio"></a>Personalizar los diseños de ventana de Visual Studio

En Visual Studio, puede personalizar la posición, el tamaño y el comportamiento de las ventanas para crear los diseños de ventana que mejor funcionen con los distintos flujos de trabajo de desarrollo. Al personalizar el diseño, el IDE lo recuerda. Por ejemplo, si cambia la ubicación de acoplamiento del **Explorador de soluciones** y después cierra Visual Studio, la próxima vez que lo abra, aunque trabaje en otro equipo, el **Explorador de soluciones** estará acoplado en la misma ubicación.

También puede asignar un nombre al diseño personalizado, guardarlo y luego cambiar de un diseño a otro con un solo comando. Por ejemplo, puede crear un diseño para la edición y otro para la depuración, y cambiar de un diseño a otro mediante el comando de menú **Ventana** > **Aplicar diseño de ventana**.

## <a name="tool-and-document-windows"></a>Ventanas de herramientas y documentos

El IDE incluye dos tipos básicos de ventanas, las *ventanas de herramientas* y las *ventanas de documento*. Entre las ventanas de herramientas están el **Explorador de soluciones**, el **Explorador de servidores**, la **Ventana de salida**, la **Lista de errores**, los diseñadores, las ventanas del depurador, etc. Las ventanas de documento contienen archivos de código fuente, archivos de texto arbitrarios, archivos de configuración, etc. Las ventanas de herramientas se pueden cambiar de tamaño y arrastrar por la barra de título. Las ventanas de documento se pueden arrastrar mediante la pestaña. Haga clic con el botón derecho en la barra de título o pestaña para establecer otras opciones en la ventana.

El menú **Ventana** muestra las opciones para acoplar, hacer flotante y ocultar ventanas en el IDE. Haga clic con el botón derecho en una pestaña de ventana o en la barra de título para ver las opciones adicionales de esa ventana concreta. Puede mostrar más de una instancia de determinadas ventanas de herramientas a la vez. Por ejemplo, puede mostrar más de una ventana del explorador web y crear instancias adicionales de algunas ventanas de herramientas eligiendo **Nueva ventana** en el menú **Ventana** .

### <a name="split-windows"></a>Ventanas divisoras

Cuando tiene que ver o editar dos ubicaciones a la vez en un documento, puede dividir las ventanas. Para dividir el documento en dos secciones con desplazamiento independiente, haga clic en **Dividir** en el menú **Ventana** . Haga clic en **Quitar división** en el menú **Ventana** para restaurar la vista única.

### <a name="tabs"></a>Tabulaciones

Puede usar pestañas para organizar el diseño de varias maneras diferentes. Por ejemplo, puede ver una vista previa de un archivo en el editor sin abrir el archivo, agrupar las pestañas, etc.

#### <a name="preview-tab-document-windows"></a>Ficha Vista previa (ventanas de documento)

En la pestaña **Vista previa**, puede ver los archivos en el editor sin abrirlos. Puede obtener una vista previa de los archivos eligiéndolos en el **Explorador de soluciones**, al depurar los archivos paso a paso por instrucciones, con **Ir a definición** y cuando se desplaza por los resultados de la búsqueda. La vista previa de los archivos aparece en una ficha en el lado derecho de la ficha de documento. El archivo se abre para su edición si lo modifica o elige la opción **Abrir**.

::: moniker range="vs-2019"

#### <a name="vertical-document-tabs"></a>Pestañas de documentos verticales

**[Nuevo en la versión 16.4](/visualstudio/releases/2019/release-notes-v16.4/)** : hemos agregado una de las principales solicitudes de características, [pestañas de documentos verticales](https://developercommunity.visualstudio.com/idea/467369/vertical-group-tab.html), en Visual Studio 2019 versión 16.4. Ahora puede administrar las pestañas de documentos en una lista vertical en el lado izquierdo o derecho del editor.

Puede aplicar pestañas de documentos verticales de las siguientes formas:

- Elija **Herramientas** > **Opciones** > **Entorno** > **Pestañas y Windows** en la barra de menús. A continuación, en el control **Establecer diseño de pestaña**, elija **Superior**, **Izquierda** o **Derecha** en la lista desplegable.

- Haga clic con el botón derecho en una pestaña, elija **Establecer diseño de pestaña** y, a continuación, elija **Izquierda** o **Derecha** (para devolver las pestañas a su posición predeterminada, elija **Superior**).

    :::image type="content" source="./media/vs-2019/vertical-tabs.gif" alt-text="Animación que muestra las pestañas de documentos verticales en acción":::

::: moniker-end

#### <a name="tab-groups"></a>Grupos de pestañas

Los grupos de pestañas mejoran su capacidad de administrar un área de trabajo reducida mientras trabaja con dos o más documentos abiertos en el IDE. Puede organizar varias ventanas de documento y ventanas de herramientas en grupos de pestañas horizontales o verticales e intercambiar documentos de un grupo a otro.

### <a name="toolbars"></a>Barras de herramientas

Puede organizar las barras de herramientas arrastrándolas hasta el lugar donde desea que estén, o bien mediante el cuadro de diálogo **Personalizar**. Para obtener más información sobre cómo ubicar y personalizar barras de herramientas, vea [Cómo: Personalizar menús y barras de herramientas](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md).

## <a name="arrange-and-dock-windows"></a>Ordenar y acoplar las ventanas

Las ventanas de documento y las ventanas de herramientas se pueden *acoplar* para que tengan un tamaño y ocupen una posición dentro del marco de ventana del IDE. También puede colocarlas como ventanas flotantes independientes situadas fuera del IDE.

Puede acoplar una ventana de herramientas en cualquier lugar dentro del marco del IDE. También puede acoplar algunas ventanas de herramientas como ventanas con pestañas en el marco del editor. Además, puede acoplar las ventanas de documento dentro del marco del editor y las puede anclar en su posición actual en el orden de tabulación.

También puede acoplar varias ventanas flotantes juntas para que compartan *espacio* sobre el IDE o fuera de él. Las ventanas de herramientas también se pueden ocultar o minimizar.

Puede organizar las ventanas de la siguiente manera:

- Ancle las ventanas de documento a la izquierda del cuadro de pestañas.

- Acople las ventanas por pestañas en el marco de edición.

- Acople las ventanas de herramientas al borde de un marco en el IDE.

- Haga flotar las ventanas de documento o de herramientas sobre el IDE o fuera de él.

- Oculte las ventanas de herramientas en el borde del IDE.

- Muestre las ventanas en distintos monitores.

- Restablezca el diseño predeterminado de ubicación de las ventana o un diseño personalizado que haya guardado.

Para organizar las ventanas de herramientas y de documento, puede colocar el cursor en la barra de título de una ventana y, a continuación, arrastrarla hasta el lugar donde desea que esté. También puede hacer clic con el botón derecho en la barra de título de la ventana para usar su menú contextual, o bien puede usar los comandos del menú **Ventana**.

### <a name="dock-windows"></a>Acoplar ventanas

Al hacer clic y arrastrar la barra de título de una ventana de herramientas o la pestaña de una ventana de documento, aparece un rombo de guía. Durante la operación de arrastre, cuando el cursor del ratón se encuentra sobre una de las flechas del rombo, aparece un área sombreada que muestra dónde se acoplará la ventana al soltar el botón del ratón.

Para mover una ventana acoplable sin ajustarla en su lugar, presione la tecla **Ctrl** mientras arrastra la ventana.

Para devolver una ventana de herramientas o una ventana de documento al punto de acoplamiento más reciente, presione **Ctrl** mientras hace doble clic en la barra de título o en la pestaña de la ventana.

La siguiente ilustración muestra el rombo de guía para las ventanas de documento que solo se pueden acoplar dentro del marco de edición:

![Rombos de guía de ventana de documento](../ide/media/documentwindowguidediamonds.png)

Las ventanas de herramientas se pueden fijar a un lado de un marco del IDE o en el marco de edición. Cuando se arrastra una ventana de herramientas a otra ubicación, aparece un rombo de guía para ayudarle a volver a acoplar la ventana.

![Rombos de guía de ventanas de herramientas](../ide/media/vs10guidediamond.png)

La siguiente ilustración muestra cómo se acopla el **Explorador de soluciones** en una nueva ubicación que está demarcada por el área sombreada en azul:

![Acoplar el Explorador de soluciones en una nueva posición](../ide/media/vs2015_dock_diamond.png)

### <a name="close-and-auto-hide-tool-windows"></a>Cerrar y ocultar automáticamente las ventanas de herramientas

Puede cerrar una ventana de herramientas haciendo clic en la **X** de la esquina superior derecha de la barra de título. Para volver a abrir la ventana, utilice el método abreviado de teclado o el comando de menú correspondiente. Las ventanas de herramientas admiten una característica denominada *Ocultar automáticamente*, lo que hace que una ventana se deslice fuera de la vista cuando se utiliza una ventana diferente. Cuando una ventana se oculta automáticamente, su nombre aparece en una pestaña situada en el borde del IDE. Para utilizar la ventana de nuevo, haga clic sobre la pestaña para que vuelva a aparecer la ventana.

![Ocultar automáticamente](../ide/media/vs2015_auto_hide.png)

> [!NOTE]
> Para establecer si Ocultar automáticamente se aplica a las ventanas de herramientas por separado o como grupos acoplados, active o desactive la opción **El botón Ocultar automáticamente afecta solo a las ventanas de herramientas activas** en el cuadro de diálogo **Opciones**. Para obtener más información, consulta [General, Entorno, Opciones (Cuadro de diálogo)](../ide/reference/general-environment-options-dialog-box.md).

> [!NOTE]
> Las ventanas de herramientas que tienen habilitada la opción Ocultar automáticamente pueden deslizarse temporalmente en la vista cuando la ventana tiene el foco. Para volver a ocultar la ventana, seleccione un elemento fuera de la ventana actual. Cuando la ventana pierde el foco, vuelve a desaparecer.

### <a name="use-a-second-monitor"></a>Usar un segundo monitor

Si tiene un segundo monitor y su sistema operativo lo admite, puede elegir qué monitor muestra una ventana. Incluso puede agrupar varias ventanas en *espacios compartidos* en otros monitores.

> [!TIP]
> Puede crear varias instancias del **Explorador de soluciones** y moverlas a otro monitor. Haga clic con el botón derecho en la ventana y elija **Nueva vista del explorador de soluciones**. Para devolver todas las ventanas al monitor original, haga doble clic mientras presiona la tecla **Ctrl**.

### <a name="reset-name-and-switch-between-window-layouts"></a>Restablecer el nombre y cambiar entre los diseños de ventana

Puede devolver el IDE al diseño de ventana original de la colección de valores de configuración mediante el comando **Restablecer diseño de ventana** . Al ejecutar este comando, se producen las siguientes acciones:

- Todas las ventanas se mueven a sus posiciones predeterminadas.

- Las ventanas que estén cerradas en el diseño de ventana predeterminado se cierran.

- Las ventanas que estén abiertas en el diseño de ventana predeterminado se abren.

### <a name="create-and-save-custom-layouts"></a>Crear y guardar los diseños personalizados

Visual Studio le permite guardar hasta 10 diseños de ventana personalizados y cambiar rápidamente de uno a otro. En los siguientes pasos le enseñamos a crear, guardar, invocar y administrar diseños personalizados que aprovechan varios monitores con ventanas de herramientas acopladas y flotantes.

Primero, vamos a crear una solución de prueba que tiene dos proyectos, cada uno con un diseño óptimo diferente.

#### <a name="create-a-ui-project-and-customize-the-layout"></a>Crear un proyecto de UI y personalizar el diseño

1. Cree un proyecto **Aplicación WPF** de C#. Imagine que, en este proyecto, va a desarrollar una interfaz de usuario. Desea maximizar el espacio de la ventana del diseñador y quitar otras ventanas de herramientas de la vista.

2. Si tiene varios monitores, coloque la ventana **Explorador de soluciones** y la ventana **Propiedades** en el segundo monitor. En un solo sistema de monitor, cierre todas las ventanas menos el diseñador.

3. Presione **Ctrl**+**Alt**+**X** para mostrar el **cuadro de herramientas**. Si la ventana se acopla, arrástrela para que flote hasta llegar al lugar donde quiere colocarla.

4. Presione **F5** para poner Visual Studio en el modo de depuración. Ajuste la posición de las ventanas **Automático**, **Pila de llamadas** y **Salida** según sus preferencias. El diseño que va a crear se aplicará al modo de edición y al de depuración.

5. Cuando sus diseños en el modo de depuración y el modo de edición estén a su gusto, seleccione **Ventana** > **Guardar diseño de ventana**. Llame a este diseño "Diseñador".

     Al nuevo diseño se le asigna el método abreviado de teclado siguiente de la lista reservada de **Ctrl**+**Alt**+**1...0**.

#### <a name="create-a-database-project-and-layout"></a>Crear un diseño y un proyecto de base de datos

1. Agregue un nuevo proyecto **Base de datos de SQL Server** a la solución.

2. Haga clic con el botón derecho en el proyecto nuevo en el **Explorador de soluciones** y elija **Ver en el explorador de objetos**. Esto muestra la ventana **Explorador de objetos de SQL Server** , desde donde puede obtener acceso a tablas, vistas y otros objetos de su base de datos. Puede hacer que esta ventana flote o dejarla acoplada. Ajuste las otras ventanas de herramientas como quiera. Si quiere, puede agregar una base de datos real, pero no es necesario para este tutorial.

3. Cuando el diseño sea de su agrado, pulse **Ventana** > **Guardar diseño de ventana** en el menú principal. Llame a este diseño "Proyecto de BD". (En este proyecto no pondremos un diseño de modo de depuración).

#### <a name="switch-between-the-layouts"></a>Cambiar entre diseños

Para cambiar entre diseños, use los métodos abreviados de teclado o pulse **Ventana** > **Aplicar diseño de ventana** en el menú principal.

![Aplicar menú de diseño de ventana](../ide/media/vs2015_applywindowlayout.png)

Después de aplicar el diseño de UI, fíjese en que el diseño se conserva en el modo de edición y en el modo de depuración.

Si tiene una configuración de varios monitores en el trabajo y un portátil en casa, puede crear diseños optimizados para cada máquina.

> [!NOTE]
> Si aplica un diseño de varios monitores en un sistema de un solo monitor, las ventanas flotantes que coloque en el segundo monitor aparecerán ocultas detrás de la ventana de Visual Studio. Para llevar estas ventanas al frente, presione **Alt + Tab**. Si luego abre Visual Studio con varios monitores, puede restaurar las ventanas a sus posiciones especificadas volviendo a aplicar el diseño.

#### <a name="manage-and-roam-your-layouts"></a>Administrar y transmitir los diseños

Para quitar, cambiar el nombre o reordenar el diseño personalizado, pulse **Ventana** > **Administrar diseños de ventana**. Si mueve un diseño, el enlace de teclado se ajusta automáticamente para reflejar la nueva posición en la lista. Los enlaces no se pueden modificar de otra forma, por lo que se puede almacenar un máximo de 10 diseños a la vez.

![Administrar los diseños de la ventana](../ide/media/managewindowlayouts.png)

Para recordar el método abreviado de teclado que está asignado a cada diseño, pulse **Ventana** > **Aplicar diseño de ventana**.

Estos diseños se transmiten automáticamente entre las ediciones de Visual Studio, entre las instancias de Blend que hay en máquinas independientes y de cualquier edición de Express a cualquier otra organización de Express. Sin embargo, los diseños no se transmiten entre Visual Studio, Blend y Express.

## <a name="see-also"></a>Consulte también

- [Cómo: Moverse por el IDE](../ide/how-to-move-around-in-the-visual-studio-ide.md)
