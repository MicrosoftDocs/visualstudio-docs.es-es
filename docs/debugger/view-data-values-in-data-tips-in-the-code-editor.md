---
title: Ver los valores de variable en la información sobre datos | Microsoft Docs
ms.custom: seodec18
ms.date: 11/21/2018
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c84c6c9049fe11de16267267df86c88851cfcdfe
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 12/07/2018
ms.locfileid: "53066855"
---
# <a name="view-data-values-in-datatips-in-the-code-editor"></a>Ver valores de datos en la información sobre datos en el editor de código

La Información sobre datos es una manera útil de ver información sobre las variables del programa durante la depuración. La Información sobre datos funciona únicamente en modo de interrupción y únicamente con las variables que están dentro del actual ámbito de ejecución. Si se trata de la primera vez que ha probado para depurar el código, es posible que desea leer [corregir errores al escribir mejor C# código](../debugger/write-better-code-with-visual-studio.md) y [de depuración para principiantes absolutos](../debugger/debugging-absolute-beginners.md) antes de pasar a través de este artículo.

Si se trata de la primera vez que la depuración, es posible que desee leer [escribir mejor C# código con Visual Studio](../debugger/write-better-code-with-visual-studio.md) y [de depuración para principiantes absolutos](../debugger/debugging-absolute-beginners.md) antes de leer este artículo.
  
## <a name="work-with-datatips"></a>Trabajar con información sobre datos

Información sobre datos solo aparece en modo de interrupción y solo en las variables que se encuentran en el ámbito actual de ejecución.

### <a name="display-a-datatip"></a>Mostrar una información sobre datos  
  
1. Establezca un punto de interrupción en el código e iniciar la depuración presionando **F5** o seleccionando **depurar** > **Iniciar depuración**.
  
1. Cuando se pausa en el punto de interrupción, mantenga el mouse sobre cualquier variable en el ámbito actual. Aparece una información sobre datos, que muestra el nombre y el valor actual de la variable.

### <a name="make-a-datatip-transparent"></a>Convertir en transparente una información sobre datos  

Para hacer una información sobre datos transparente para ver el código que está debajo de él, mientras que en la información sobre datos, presione **Ctrl**. La información sobre datos permanecerá transparente mientras mantiene presionada la **Ctrl** clave. Esto no funciona para información sobre datos anclada o flota.  
### <a name="pin-a-datatip"></a>Anclar una información sobre datos

Para anclar una información sobre datos para que permanezca abierta, seleccione la chincheta **anclar a origen** icono. 

![Anclar una información sobre datos](../debugger/media/dbg-tips-data-tips-pinned.png "anclar una información sobre datos")

Puede mover una información sobre datos anclada arrastrando en torno a la ventana de código. Aparece un icono de chincheta en el medianil junto a la línea de a que la información sobre datos está anclado. 

>[!NOTE]
>Información sobre datos siempre se evalúa en el contexto donde se suspende la ejecución, no el cursor actual o la ubicación de la información sobre datos. Si mantiene el puntero sobre una variable en otra función que tiene el mismo nombre que una variable en el contexto actual, se muestra el valor de la variable en el contexto actual.
  
### <a name="unpin-a-datatip-from-source"></a>Desanclar la información sobre datos de origen

Para hacer flotar una información sobre datos anclada, mantenga el mouse sobre la información sobre datos y seleccione el icono de chincheta en el menú contextual. 

El icono de alfiler cambia a la posición desanclada y la información sobre datos flota ahora o se puede arrastrar ventanas abiertas por encima de todo. La información sobre datos flotante se cierre cuando finaliza la sesión de depuración.  
  
### <a name="repin-a-datatip"></a>Anclar una información sobre datos  
  
Para anclar una información sobre datos flotante al origen, sitúe el puntero sobre él en el editor de código y seleccione el icono de chincheta. El icono de alfiler cambia a la posición anclada y nuevo está anclada la información sobre datos solo a la ventana de código. 

Si una información sobre datos flota sobre una ventana de código que no sean de origen, el icono de PIN no está disponible y no puede ser vuelto a anclar la información sobre datos. Para tener acceso al icono de chincheta, devolver la información sobre datos a la ventana del editor de código arrastrarla o dar el foco de la ventana de código. 
  
### <a name="close-a-datatip"></a>Cerrar una información sobre datos  
  
Para cerrar una información sobre datos, mantenga el mouse sobre la información sobre datos y seleccione Cerrar (**x**) icono en el menú contextual.  
  
### <a name="close-all-datatips"></a>Cierre todas las sugerencias de datos  
  
Para cerrar la información sobre todos los datos, en el **depurar** menú, seleccione **borrar todas las sugerencias de datos**.  
  
### <a name="close-all-datatips-for-a-specific-file"></a>Cierre todas las sugerencias de datos para un archivo específico  
  
Para cerrar todas las sugerencias de datos para un archivo específico, en el **depurar** menú, seleccione **borrar todos los información sobre datos anclada a \<Filename >**.  
  
## <a name="expand-and-edit-information"></a>Expandir y editar información  
Con la Información sobre datos, se puede expandir una matriz, una estructura o un objeto para ver sus miembros. También se puede editar el valor de una variable de una Información sobre datos.  
  
### <a name="expand-a-variable"></a>Expandir una variable

Para expandir un objeto en una información sobre datos para ver sus elementos, mantenga el mouse sobre las flechas de expansión antes de los nombres de elemento para mostrar los elementos en forma de árbol. Para una información sobre datos anclada, seleccione el **+** antes de la variable de nombre y, a continuación, expanda el árbol. 

![Expanda una información sobre datos](../debugger/media/dbg-tour-data-tips.png "expandir una información sobre datos")

Puede usar el mouse o las teclas de flecha del teclado para mover hacia arriba y abajo en la vista ampliada. 

También puede anclar elementos expandidos a la información sobre datos anclada al mantener el mouse sobre ellos y seleccionando sus iconos de marcador. Los elementos aparecen a continuación, en la información sobre datos anclada después de contrae el árbol. 

### <a name="edit-the-value-of-a-variable"></a>Edite el valor de una variable

Para editar el valor de una variable o un elemento en una información sobre datos, seleccione el valor, escriba un nuevo valor y presione **ENTRAR**. Selección está deshabilitada para los valores de solo lectura.  

## <a name="visualize-complex-data-types"></a>Visualizar tipos de datos complejos  

Un icono de lupa junto a una variable o un elemento en una información sobre datos significa que uno o más [visualizadores](../debugger/create-custom-visualizers-of-data.md), como el [visualizador de texto](../debugger/string-visualizer-dialog-box.md), están disponibles para la variable. Los visualizadores de mostrar información de una manera más significativa, a veces, gráfica.
  
Para ver el elemento con el visualizador predeterminado para el tipo de datos, seleccione el icono de lupa ![icono visualizador](../debugger/media/dbg-tips-visualizer-icon.png "icono visualizador"). Seleccione la flecha situada junto al icono de lupa para seleccionar de una lista de visualizadores para el tipo de datos.  

## <a name="add-a-variable-to-a-watch-window"></a>Agregar una variable a una ventana Inspección  

Si desea seguir examinando una variable, puede agregarlo a un **inspección** ventana desde una información sobre datos. Haga clic en la variable en la información sobre datos y seleccione **Agregar inspección**. 

La variable aparece en el **inspección** ventana. Si la edición de Visual Studio admite más de un **inspección** ventana, la variable aparece en **Inspección 1**. 
  
## <a name="import-and-export-datatips"></a>Importar y exportar información sobre datos  

Puede exportar información sobre datos a un archivo XML, que puede compartir o editar con un editor de texto. También puede importar un archivo DataTip XML ha recibido o editado. 
  
**Para exportar información sobre datos:** 
  
1. Seleccione **depurar** > **exportar información sobre datos**.  
   
1. En el **exportar información sobre datos** cuadro de diálogo, vaya a la ubicación para guardar el archivo XML, escriba un nombre para el archivo y, a continuación, seleccione **guardar**.  
  
**Para importar información sobre datos:** 
  
1. Seleccione **depurar** > **importar información sobre datos**.  
   
1. En el **importar información sobre datos** cuadro de diálogo, seleccione el archivo de DataTips XML que desea abrir y, a continuación, seleccione **abrir**.  

## <a name="see-also"></a>Vea también  
 [¿Qué es la depuración?](../debugger/what-is-debugging.md)  
 [Corrección de errores escribiendo mejor código de C#](../debugger/write-better-code-with-visual-studio.md)  
 [Primer vistazo al depurar](../debugger/debugger-feature-tour.md) [ver datos en el depurador](../debugger/viewing-data-in-the-debugger.md)   
 [Ventanas Inspección e Inspección rápida](../debugger/watch-and-quickwatch-windows.md)   
 [Create Custom Visualizers](../debugger/create-custom-visualizers-of-data.md) (Crear visualizadores personalizados)   

