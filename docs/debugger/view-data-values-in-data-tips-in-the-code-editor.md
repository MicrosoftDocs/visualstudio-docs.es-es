---
title: Consulta de valores de variables en la Información sobre datos | Microsoft Docs
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
ms.openlocfilehash: bf5eda8205dbe0629d0b2801473de83c2f91257e
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/25/2019
ms.locfileid: "75404281"
---
# <a name="view-data-values-in-datatips-in-the-code-editor"></a>Consulta de valores en la Información sobre datos en el editor de código

La Información sobre datos es una manera útil de ver información sobre las variables del programa durante la depuración. La Información sobre datos funciona únicamente en modo de interrupción y únicamente con las variables que están dentro del actual ámbito de ejecución. Si esta es la primera vez que intenta depurar código, le recomendamos que lea [Cómo depurar para principiantes sin experiencia](../debugger/debugging-absolute-beginners.md) y [Herramientas y técnicas de depuración](../debugger/write-better-code-with-visual-studio.md) antes de continuar con este artículo.

## <a name="work-with-datatips"></a>Trabajo con la Información sobre datos

La Información sobre datos aparece únicamente en modo de interrupción y solo con las variables que están dentro del actual ámbito de ejecución.

### <a name="display-a-datatip"></a>Consulta de la Información sobre información

1. Establezca un punto de interrupción en el código e inicie la depuración presionando **F5** o seleccionando **Depurar** > **Iniciar depuración**.

1. Cuando pause el punto de interrupción, mantenga el puntero sobre cualquier variable del ámbito actual. Aparecerá la Información sobre datos, en la que se mostrarán el nombre y el valor actual de la variable.

### <a name="make-a-datatip-transparent"></a>Configuración de una Información sobre datos como transparente

Para que la Información sobre datos sea transparente y ver el código que está debajo, mientras se encuentra en la Información sobre datos, presione **Ctrl**. La Información sobre datos permanecerá transparente mientras mantenga presionada la tecla **Ctrl**. Esto no funciona para una Información sobre datos anclada o flotante.
### <a name="pin-a-datatip"></a>Anclado de una Información sobre datos

Para anclar una Información sobre datos de modo que permanezca abierta, seleccione el icono de marcador **Anclar al origen**.

![Anclado de una Información sobre datos](../debugger/media/dbg-tips-data-tips-pinned.png "Anclado de una Información sobre datos")

Puede mover la Información sobre datos anclada arrastrándola alrededor de la ventana de código. Aparece un icono de marcador en el medianil junto a la línea a la que está anclada la Información sobre datos.

>[!NOTE]
>Las informaciones sobre datos siempre se evalúan en el contexto en el que se suspende la ejecución, y no con respecto al cursor actual o la ubicación de la Información sobre datos. Si mantiene el cursor sobre una variable en otra función que tenga el mismo nombre que una variable en el contexto actual, se mostrará el valor de la variable del contexto actual.

### <a name="unpin-a-datatip-from-source"></a>Desanclado de una Información sobre datos del origen

Para hacer que una Información sobre datos anclada sea flotante, mantenga el puntero sobre la Información sobre datos y seleccione el icono de marcador en el menú contextual.

El icono de marcador cambia a la posición desanclada y la Información sobre datos ahora es flotante o se puede arrastrar encima de las ventanas abiertas. La Información sobre datos que flota se cierra cuando la sesión de depuración finaliza.

### <a name="repin-a-datatip"></a>Reanclado de una Información sobre datos

Para volver a anclar una Información sobre datos flotante al origen, mantenga el puntero sobre ella en el editor de código y seleccione el icono de marcador. El icono de marcador cambia a la posición anclada y la Información sobre datos se vuelve a anclar solo a la ventana de código.

Si la Información sobre datos está flotando sobre una ventana que no es parte del código fuente, el icono de marcador no estará disponible y la Información sobre datos no se podrá volver a anclar. Para acceder al icono de marcador, vuelva a poner la Información sobre datos de la ventana del editor de código arrastrándola o centrándose en la ventana de código.

### <a name="close-a-datatip"></a>Cierre de una Información sobre datos

Para cerrar una Información sobre datos, mantenga el puntero sobre la Información sobre datos y seleccione el icono de cierre (**x**) en el menú contextual.

### <a name="close-all-datatips"></a>Cierre de toda la Información sobre datos

Para cerrar toda la Información sobre datos, en el menú **Depurar**, seleccione **Borrar toda la información sobre datos**.

### <a name="close-all-datatips-for-a-specific-file"></a>Cierre de toda la Información sobre datos de un archivo concreto

Para cerrar toda la información sobre datos de un archivo concreto, en el menú **Depurar**, seleccione **Borrar toda la información sobre datos anclada a \<Filename>** .

## <a name="expand-and-edit-information"></a>Expansión y edición de la información
Con la Información sobre datos, se puede expandir una matriz, una estructura o un objeto para ver sus miembros. También se puede editar el valor de una variable de una Información sobre datos.

### <a name="expand-a-variable"></a>Expansión de una variable

Para expandir un objeto de una Información sobre datos y ver sus elementos, mantenga el puntero sobre las flechas para expandir delante de los nombres de elementos para mostrar los elementos en forma de árbol. Para una Información sobre datos anclada, seleccione **+** , antes del nombre de la variable y, a continuación, expanda el árbol.

![Expansión de una información sobre datos](../debugger/media/dbg-tour-data-tips.png "Expansión de una Información sobre datos")

Puede utilizar el mouse o las teclas de dirección en el teclado para desplazarse de arriba abajo en la vista expandida.

También puede anclar los elementos expandidos a la Información sobre datos anclada manteniendo el puntero sobre ellos y seleccionando sus iconos de marcador. Los elementos aparecen en la Información sobre datos anclada después de contraerse el árbol.

### <a name="edit-the-value-of-a-variable"></a>Edición del valor de una variable

Para editar el valor de una variable o un elemento en una Información sobre datos, seleccione el valor, escriba uno nuevo y presione **Entrar**. La selección está deshabilitada en los valores de solo lectura.

::: moniker range=">= vs-2019"

## <a name="pin-properties-in-datatips"></a>Anclado de propiedades en la Información sobre datos

> [!NOTE]
> Esta característica se admite en .NET Core 3.0 o versiones posteriores.

Puede inspeccionar rápidamente los objetos según sus propiedades en la Información sobre datos con la **herramienta para anclar propiedades**.  Para usar esta herramienta, mantenga el puntero sobre una propiedad y seleccione el icono para anclar que aparece o haga clic con el botón derecho y seleccione la opción **Anclar miembro como favorito** en el menú contextual resultante.  Esta propiedad se propaga a la parte superior de la lista de propiedades del objeto, y el nombre y el valor de la propiedad se muestran en la columna derecha de la Información sobre datos.  Para desanclar una propiedad, vuelva a seleccionar el icono para anclar o seleccione la opción **Desanclar miembro como favorito** en el menú contextual.

![Anclado de una propiedad en una Información sobre datos](../debugger/media/basic-pin-datatip.gif "Anclado de una propiedad en una Información sobre datos")

También puede alternar los nombres de propiedades y filtrar las no ancladas al consultar la lista de propiedades del objeto en una Información sobre datos.  Para acceder a cualquiera de las opciones, haga clic con el botón derecho en una fila que contenga una propiedad y seleccione las opciones **Mostrar solo miembros anclados** u **Ocultar nombres de miembros anclados en valores** en el menú contextual.

::: moniker-end

## <a name="visualize-complex-data-types"></a>Visualización de tipos de datos complejos

Un icono de lupa situado junto a una variable o un elemento de una Información sobre datos significa que uno o varios [visualizadores](../debugger/create-custom-visualizers-of-data.md), como el [Visualizador de texto](../debugger/string-visualizer-dialog-box.md), están disponibles para la variable. Los visualizadores muestran información en un modo más significativo y, a veces, más gráfico.

Para ver el elemento con el visualizador predeterminado del tipo de datos, seleccione el icono de lupa ![Icono del visualizador](../debugger/media/dbg-tips-visualizer-icon.png "Icono del visualizador"). Seleccione la flecha situada junto al icono de lupa para seleccionarlo en una lista de visualizadores para el tipo de datos.

## <a name="add-a-variable-to-a-watch-window"></a>Adición de una variable a la ventana Inspección

Si quiere seguir examinando una variable, puede agregarla a una ventana **Inspección** desde la Información sobre datos. Haga clic con el botón derecho en la variable en la Información sobre datos y seleccione **Agregar inspección**.

La variable aparece en la ventana  **Inspección**. Si la edición de Visual Studio admite más de una ventana **Inspección**, la variable aparece en **Inspección 1**.

## <a name="import-and-export-datatips"></a>Importación y exportación de Información sobre datos

Puede exportar Información sobre datos en un archivo XML que puede compartir o editar mediante un editor de texto. También puede importar un archivo XML de Información sobre datos que haya recibido o editado.

**Para exportar información sobre datos:**

1. Seleccione **Depurar** > **Exportar información sobre datos**.

1. En el cuadro de diálogo **Exportar información sobre datos**, vaya a la ubicación para guardar el archivo XML, escriba un nombre para el archivo y, a continuación, seleccione **Guardar**.

**Para importar información sobre datos:**

1. Seleccione **Depurar** > **Importar información sobre datos**.

1. En el cuadro de diálogo **Importar información sobre datos**, seleccione el archivo XML de Información sobre datos que quiera abrir y, a continuación, seleccione **Abrir**.

## <a name="see-also"></a>Vea también
- [¿Qué es la depuración?](../debugger/what-is-debugging.md)
- [Herramientas y técnicas de depuración](../debugger/write-better-code-with-visual-studio.md)
- [Primer vistazo a la depuración](../debugger/debugger-feature-tour.md)
- [Ver datos en el depurador](../debugger/viewing-data-in-the-debugger.md)
- [Ventanas Inspección e Inspección rápida](../debugger/watch-and-quickwatch-windows.md)
- [Create Custom Visualizers](../debugger/create-custom-visualizers-of-data.md) (Crear visualizadores personalizados)
