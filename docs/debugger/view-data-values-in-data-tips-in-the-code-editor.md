---
title: "Ver valores de datos de información sobre datos en el editor de código | Documentos de Microsoft"
ms.custom: 
ms.date: 07/14/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "38"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2eb975b5d4c1f3450ca18b1ea0da3cd3b7fb6375
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="view-data-values-in-datatips-in-the-code-editor"></a>Ver valores de datos de información sobre datos en el editor de código
La Información sobre datos es una manera útil de ver información sobre las variables del programa durante la depuración. La Información sobre datos funciona únicamente en modo de interrupción y únicamente con las variables que están dentro del actual ámbito de ejecución.
  
### <a name="to-display-a-datatip"></a>Para mostrar una información sobre datos  
  
1. Establecer un punto de interrupción e inicie la depuración (presione **F5**).

2. Cuando está en pausa en el depurador, coloque el puntero del mouse sobre cualquier variable en el ámbito actual.
  
     Aparece la Información sobre datos.
  
3.  La Información sobre datos desaparece al quitar el puntero del mouse. Para anclar la información sobre datos para que permanezca abierta, haga clic en el **anclar a origen** icono o botón secundario en una variable, a continuación, haga clic en **anclar a origen**.

    ![Fijar una sugerencia de datos](../debugger/media/dbg-tips-data-tips-pinned.png "PinningDataTip")

    > [!NOTE]
    > Las informaciones sobre datos siempre se evalúan en el contexto en el que se suspende la ejecución, y no en el que el cursor se mantiene sobre un elemento. Si mantiene el cursor sobre una variable en otra función con el mismo nombre que una variable que está en el contexto actual, el valor de la variable de la otra función se mostrará como el valor de la variable del contexto actual.
  
### <a name="to-unpin-a-datatip-and-make-it-float"></a>Desanclar la Información sobre datos y dejar que flote  
  
-   En una información sobre datos anclada, haga clic en el **Desanclar del origen** icono.  
  
     El icono pasa a la posición desanclada. La Información sobre datos flota ahora sobre las ventanas abiertas. La Información sobre datos que flota se cierra cuando la sesión de depuración finaliza.  
  
### <a name="to-repin-a-floating-datatip"></a>Para volver a anclar una Información sobre datos flotante  
  
-   En una Información sobre datos, haga clic en el icono de anclaje.  
  
     El icono pasa a la posición anclada. Si la Información sobre datos está fuera de una ventana de código fuente, el icono está deshabilitado y no se puede anclar.  
  
### <a name="to-close-a-datatip"></a>Para cerrar una Información sobre datos  
  
-   Coloque el puntero del mouse sobre una información sobre datos y, a continuación, haga clic en el **cerrar** icono.  
  
### <a name="to-close-all-datatips"></a>Para cerrar toda la Información sobre datos  
  
-   En el **depurar** menú, haga clic en **borrar la información sobre datos todos los**.  
  
### <a name="to-close-all-datatips-for-a-specific-file"></a>Para cerrar toda la información sobre datos de un archivo concreto  
  
-   En el **depurar** menú, haga clic en **desactive todos los información sobre datos anclada en** *archivo*.  
  
## <a name="expand-and-edit-information"></a>Expandir y editar información  
 Con la Información sobre datos, se puede expandir una matriz, una estructura o un objeto para ver sus miembros. También se puede editar el valor de una variable de una Información sobre datos.  
  
#### <a name="to-expand-a-variable-to-see-its-elements"></a>Para expandir una variable y ver sus elementos  
  
-   En una información sobre datos, coloque el puntero del mouse sobre la  **+**  inicio de sesión que precede al nombre de variable.  
  
    La variable se expande y se muestran sus elementos en forma de árbol.

    ![Ver información sobre datos](../debugger/media/dbg-tour-data-tips.gif "ver una sugerencia de datos")
  
    Cuando la variable está expandida, puede utilizar las teclas de dirección en el teclado para desplazarse de arriba abajo. También puede utilizar el mouse.  
  
#### <a name="to-edit-the-value-of-a-variable-using-a-datatip"></a>Para modificar el valor de una variable mediante la Información sobre datos  
  
1.  En una Información sobre datos, haga clic en el valor. En los valores de solo lectura, no está habilitado.  
  
2.  Escriba el nuevo valor y presione ENTRAR.  
  
## <a name="making-a-datatip-transparent"></a>Configurar una Información sobre datos como transparente  
 Si desea ver el código que está detrás de una Información sobre datos, puede configurar temporalmente dicha información como transparente. Esto no se aplica a la información sobre datos cuando está anclada o flota.  
  
#### <a name="to-make-a-datatip-transparent"></a>Para configurar una Información sobre datos como transparente  
  
-   En una Información sobre datos, presione CTRL.  
  
     La Información sobre datos permanecerá transparente mientras mantenga presionada la tecla CTRL.  
  
## <a name="visualize-complex-data-types"></a>Visualizar tipos de datos complejos  
 Si aparece un icono de lupa situado junto a un nombre de variable en una información sobre datos, uno o varios [visualizadores](../debugger/create-custom-visualizers-of-data.md), como el [cadena visualizadores](../debugger/string-visualizer-dialog-box.md), están disponibles para las variables de ese tipo de datos. Los visualizadores se pueden utilizar para mostrar la información de manera más significativa, normalmente de forma gráfica.
  
#### <a name="to-view-the-contents-of-a-variable-using-a-visualizer"></a>Para ver el contenido de una variable mediante un visualizador  
  
-   Haga clic en el icono de lupa ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "icono visualizador") para seleccionar el visualizador predeterminado del tipo de datos.  
  
     O bien  
  
     Haga clic en la flecha emergente junto al visualizador para seleccionar una lista emergente de visualizadores adecuados para el tipo de datos.  
  
     Un visualizador muestra la información.  
  
## <a name="add-information-to-a-watch-window"></a>Agregar información a una ventana Inspección  
 Si desea seguir examinando una variable en una vista de lista, puede agregar la variable a la **inspección** ventana desde una información sobre datos.  
  
#### <a name="to-add-a-variable-to-the-watch-window"></a>Para agregar una variable a la ventana Inspección  
  
-   Haga clic en una información sobre datos y, a continuación, haga clic en **Agregar inspección**.  
  
     La variable se agrega a la **inspección** ventana. Si está usando una edición que admite varias **inspección** windows, la variable se agrega a **Inspección 1.**  
  
## <a name="import-and-export-datatips"></a>Importar y exportar información sobre datos  
 Puede exportar Información sobre datos a un archivo XML, que puede compartir con un colega o modificar con un editor de texto.  
  
#### <a name="to-export-datatips"></a>Para exportar información sobre datos  
  
1.  En el menú Depurar, haga clic en **exportar información sobre datos**.  
  
     El **exportar información sobre datos** aparece el cuadro de diálogo.  
  
2.  Utilizar técnicas del archivo estándar para navegar hasta la ubicación donde desea guardar el archivo XML, escriba un nombre para el archivo en el **nombre de archivo** cuadro y, a continuación, haga clic en **Aceptar**.  
  
#### <a name="to-import-datatips"></a>Para importar información sobre datos  
  
1.  En el menú Depurar, haga clic en **importar información sobre datos**.  
  
     El **importar información sobre datos** aparece el cuadro de diálogo.  
  
2.  Utilice el cuadro de diálogo para buscar el archivo XML que desea abrir y haga clic en **Aceptar**.  
  
## <a name="see-also"></a>Vea también  
 [Ver los datos en el depurador](../debugger/viewing-data-in-the-debugger.md)   
 [Inspección y ventanas de inspección rápida](../debugger/watch-and-quickwatch-windows.md)   
 [Create Custom Visualizers](../debugger/create-custom-visualizers-of-data.md) (Crear visualizadores personalizados)   