---
title: Ver valores de variables en la información sobre herramientas | Microsoft Docs
ms.custom: seodec18
ms.date: 11/21/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], DataTips
- DataTips tool
ms.assetid: ffa7bd18-439b-4685-a9b3-c7884b5de41f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f121c7aadb605e6eb87089556ddaf1b1f4999dbb
ms.sourcegitcommit: 0b90e1197173749c4efee15c2a75a3b206c85538
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/07/2019
ms.locfileid: "74903894"
---
# <a name="view-data-values-in-datatips-in-the-code-editor"></a>Ver valores de datos en la información sobre datos en el editor de código

La Información sobre datos es una manera útil de ver información sobre las variables del programa durante la depuración. La Información sobre datos funciona únicamente en modo de interrupción y únicamente con las variables que están dentro del actual ámbito de ejecución. Si es la primera vez que intenta depurar código, puede que desee leer la [depuración para principiantes absolutos](../debugger/debugging-absolute-beginners.md) y [herramientas y técnicas de depuración](../debugger/write-better-code-with-visual-studio.md) antes de pasar a este artículo.

## <a name="work-with-datatips"></a>Trabajar con información sobre herramientas

La información sobre herramientas solo aparece en modo de interrupción y solo en las variables que están en el ámbito actual de ejecución.

### <a name="display-a-datatip"></a>Mostrar una información sobre información

1. Establezca un punto de interrupción en el código e inicie la depuración presionando **F5** o seleccionando **depurar** > **iniciar depuración**.

1. Cuando se pausa en el punto de interrupción, se mantiene el mouse sobre cualquier variable del ámbito actual. Aparece una información sobre información, que muestra el nombre y el valor actual de la variable.

### <a name="make-a-datatip-transparent"></a>Convertir una información sobre información en transparente

Para que la información sobre la información sea transparente para ver el código que está debajo de ella, mientras se encuentra en la información sobre información, presione **Ctrl**. La información sobre la información permanece transparente siempre y cuando mantenga presionada la tecla **Ctrl** . Esto no funciona para la información sobre los mismos anclados o flotantes.
### <a name="pin-a-datatip"></a>Anclar una información sobre información

Para anclar una información sobre información de modo que permanezca abierta, seleccione el icono **anclar al código fuente** .

![Anclar una información sobre información](../debugger/media/dbg-tips-data-tips-pinned.png "Anclar una información sobre información")

Puede mover la información sobre la información anclada arrastrándola alrededor de la ventana de código. Aparece un icono de alfiler en el medianil junto a la línea a la que está anclada la información sobre la información.

>[!NOTE]
>Las informaciones sobre herramientas siempre se evalúan en el contexto en el que se suspende la ejecución, no en la ubicación actual del cursor o la información sobre herramientas. Si mantiene el mouse sobre una variable en otra función que tiene el mismo nombre que una variable en el contexto actual, se muestra el valor de la variable en el contexto actual.

### <a name="unpin-a-datatip-from-source"></a>Desanclar la información sobre información del origen

Para flotar una información sobre información anclada, mantenga el mouse sobre la información sobre la información y seleccione el icono de alfiler en el menú contextual.

El icono de alfiler cambia a la posición desanclada y la información sobre la información sobre las ventanas abiertas se puede arrastrar. Información sobre la información sobre herramientas flotante cierre cuando finalice la sesión de depuración.

### <a name="repin-a-datatip"></a>Volver a anclarlo información sobre la información

Para volver a anclarlo una información sobre la información flotante en el origen, mantenga el mouse sobre ella en el editor de código y seleccione el icono de alfiler. El icono de alfiler cambia a la posición anclada y la información sobre la información se vuelve a anclar solo a la ventana de código.

Si la información sobre la información está flotando sobre una ventana de código no fuente, el icono de alfiler no estará disponible y no se podrá reanclar la información sobre la información. Para tener acceso al icono de alfiler, vuelva a la información sobre la ventana del editor de código arrastrándola o concediendo el foco de la ventana de código.

### <a name="close-a-datatip"></a>Cerrar una información sobre información

Para cerrar una información sobre información, mantenga el mouse sobre la información sobre la información y seleccione el icono cerrar (**x**) en el menú contextual.

### <a name="close-all-datatips"></a>Cerrar toda la información sobre herramientas

Para cerrar toda la información sobre herramientas, en el menú **depurar** , seleccione **borrar toda la información sobre herramientas**.

### <a name="close-all-datatips-for-a-specific-file"></a>Cerrar toda la información sobre los detalles de un archivo específico

Para cerrar toda la información sobre los detalles de un archivo específico, en el menú **depurar** , seleccione **borrar toda la información sobre herramientas anclada a \<nombre de archivo >** .

## <a name="expand-and-edit-information"></a>Expandir y editar información
Con la Información sobre datos, se puede expandir una matriz, una estructura o un objeto para ver sus miembros. También se puede editar el valor de una variable de una Información sobre datos.

### <a name="expand-a-variable"></a>Expandir una variable

Para expandir un objeto de una información sobre información para ver sus elementos, mantenga el mouse sobre las flechas de expandir delante de los nombres de elemento para mostrar los elementos en forma de árbol. Para una información sobre información anclada, seleccione la **+** antes del nombre de la variable y, a continuación, expanda el árbol.

![Expandir una información sobre información](../debugger/media/dbg-tour-data-tips.png "Expandir una información sobre información")

Puede usar el mouse o las teclas de flecha del teclado para moverse hacia arriba y hacia abajo en la vista expandida.

También puede anclar los elementos expandidos a la información sobre la información anclada si mantiene el puntero sobre ellos y selecciona sus iconos de alfiler. Los elementos aparecen en la información sobre la información fija después de contraerse el árbol.

### <a name="edit-the-value-of-a-variable"></a>Editar el valor de una variable

Para editar el valor de una variable o elemento en una información sobre información, seleccione el valor, escriba un nuevo valor y presione **entrar**. La selección está deshabilitada para los valores de solo lectura.

::: moniker range=">= vs-2019"

## <a name="pin-properties-in-datatips-supported-in-visual-studio-2019-version-164-preview-3-or-higher"></a>Anclar propiedades en la información sobre los elementos de información (compatible con Visual Studio 2019 versión 16,4 Preview 3 o superior)

> [!NOTE]
> Esta característica es compatible con .NET Core 3,0 o superior.

Puede inspeccionar rápidamente objetos por sus propiedades en la información sobre herramientas con la herramienta **anclar propiedades** .  Para usar esta herramienta, mantenga el mouse sobre una propiedad y seleccione el icono de anclaje que aparece o haga clic con el botón derecho y seleccione la opción **anclar miembro como favorito** en el menú contextual resultante.  Esta propiedad se propaga a la parte superior de la lista de propiedades del objeto y el nombre y el valor de la propiedad se muestra en la columna derecha de la información sobre la información sobre la información.  Para desanclar una propiedad, vuelva a seleccionar el icono de anclaje o seleccione la opción **desanclar miembro como favorito** en el menú contextual.

![Anclar una propiedad en una información sobre información](../debugger/media/basic-pin-datatip.gif "Anclar una propiedad en una información sobre información")

También puede alternar los nombres de propiedad y filtrar las propiedades no ancladas al ver la lista de propiedades del objeto en una información sobre información.  Para tener acceso a cualquiera de las opciones, haga clic con el botón secundario en una fila que contenga una propiedad y seleccione la opción **Mostrar solo miembros anclados** u **ocultar nombres de miembros anclados en valores** del menú contextual.

::: moniker-end

## <a name="visualize-complex-data-types"></a>Visualización de tipos de datos complejos

Un icono de lupa situado junto a una variable o elemento de una información sobre información significa que uno o varios [visualizadores](../debugger/create-custom-visualizers-of-data.md), como el [visualizador de texto](../debugger/string-visualizer-dialog-box.md), están disponibles para la variable. Los visualizadores muestran información en un modo más significativo, en ocasiones gráficos.

Para ver el elemento con el visualizador predeterminado para el tipo de datos, seleccione el icono del ![visualizador](../debugger/media/dbg-tips-visualizer-icon.png "Icono del visualizador")icono de lupa. Seleccione la flecha situada junto al icono de lupa para seleccionarlo en una lista de visualizadores para el tipo de datos.

## <a name="add-a-variable-to-a-watch-window"></a>Agregar una variable a un ventana Inspección

Si desea seguir viendo una variable, puede agregarla a una ventana **inspección** desde una información sobre información. Haga clic con el botón derecho en la variable en la información sobre información y seleccione **Agregar inspección**.

La variable aparece en la ventana **inspección** . Si la edición de Visual Studio admite más de una ventana **inspección** , la variable aparece en la **inspección 1**.

## <a name="import-and-export-datatips"></a>Importar y exportar información sobre los mismos

Puede exportar información sobre herramientas a un archivo XML, que puede compartir o editar mediante un editor de texto. También puede importar un archivo XML de información sobre información que haya recibido o editado.

**Para exportar información sobre datos:**

1. Seleccione **Depurar** > **exportar información sobre herramientas**.

1. En el cuadro de diálogo **exportar información sobre herramientas** , vaya a la ubicación donde desea guardar el archivo XML, escriba un nombre para el archivo y, a continuación, seleccione **Guardar**.

**Para importar información sobre datos:**

1. Seleccione **Depurar** > **Importar información sobre herramientas**.

1. En el cuadro de diálogo **Importar información sobre herramientas** , seleccione el archivo XML de información sobre herramientas que desea abrir y, a continuación, seleccione **abrir**.

## <a name="see-also"></a>Vea también
- [¿Qué es la depuración?](../debugger/what-is-debugging.md)
- [Herramientas y técnicas de depuración](../debugger/write-better-code-with-visual-studio.md)
- [Primer vistazo a la depuración](../debugger/debugger-feature-tour.md)
- [Ver datos en el depurador](../debugger/viewing-data-in-the-debugger.md)
- [Ventanas Inspección e Inspección rápida](../debugger/watch-and-quickwatch-windows.md)
- [Create Custom Visualizers](../debugger/create-custom-visualizers-of-data.md) (Crear visualizadores personalizados)
