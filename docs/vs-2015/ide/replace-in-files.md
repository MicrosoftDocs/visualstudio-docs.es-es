---
title: Reemplazar en archivos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.findreplace.replaceinfiles
- vs.replaceinfiles
helpviewer_keywords:
- text searches, replacing text
- Find and Replace window, Replace in Files tab
- Replace in Files tab, Find and Replace window
ms.assetid: ca361466-53bd-44db-a28a-3a74bc03b028
caps.latest.revision: 33
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 001f1faa969275788b10bc9bd1e6398373a54b37
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669976"
---
# <a name="replace-in-files"></a>Reemplazar en archivos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Reemplazar en archivos** permite buscar el código de un conjunto de archivos especificado para una cadena o expresión, y cambiar algunas o todas las coincidencias que se detectan. Las coincidencias encontradas y las acciones realizadas se muestran en la ventana **Resultados de la búsqueda** seleccionada en **Opciones de resultados**.

> [!NOTE]
> Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija Importar y exportar configuraciones en el menú Herramientas. Para obtener más información, vea [Personalizar la configuración de desarrollo en Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

 Puede usar cualquiera de los métodos siguientes para mostrar **Reemplazar en archivos** en la ventana **Buscar y reemplazar**.

### <a name="to-display-replace-in-files"></a>Para mostrar Reemplazar en archivos

1. En el menú **Edición**, expanda **Buscar y reemplazar**.

2. Pulse **Reemplazar en archivos**.

     o

     Si la ventana **Buscar y reemplazar** ya está abierta, en la barra de herramientas, pulse **Reemplazar en archivos**.

## <a name="find-what"></a>Buscar
 Para buscar una nueva cadena de texto o expresión, especifíquela en el cuadro. Para buscar cualquiera de las 20 cadenas que buscó más recientemente, abra la lista y elija la cadena que desea buscar. Pulse el botón **Generador de expresiones** adyacente si quiere usar una o varias expresiones regulares en la cadena de búsqueda. Para obtener más información, vea [Usar expresiones regulares en Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

## <a name="replace-with"></a>Reemplazar por
 Para reemplazar instancias de la cadena en el cuadro **Buscar** por otra cadena, escriba la cadena de reemplazo en el cuadro **Reemplazar por**. Para eliminar instancias de la cadena en el cuadro **Buscar**, deje este campo en blanco. Abra la lista para mostrar las 20 cadenas que ha buscado más recientemente. Pulse el botón **Generador de expresiones** adyacente si quiere usar una o varias expresiones regulares en la cadena de reemplazo. Para obtener más información, vea [Usar expresiones regulares en Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

## <a name="look-in"></a>Buscar en
 La opción elegida en la lista desplegable **Buscar en** determina si **Reemplazar en archivos** solo busca en los archivos activos actualmente o en todos los archivos almacenados en algunas carpetas. Seleccione un ámbito de búsqueda en la lista, escriba una ruta de carpeta o haga clic en el botón **Examinar (...)** para mostrar el cuadro de diálogo **Elegir carpetas de búsqueda** y seleccionar un conjunto de carpetas para buscar. También puede escribir una ruta directamente en el cuadro **Buscar en**.

> [!NOTE]
> Si la opción **Buscar en** seleccionada conlleva buscar en un archivo que ha desprotegido desde el control de código fuente, solo se busca en la versión de ese archivo que se ha descargado en el equipo local.

## <a name="find-options"></a>Opciones de búsqueda
 Puede expandir o contraer la sección **Opciones de búsqueda**. Se pueden activar o desactivar las opciones siguientes:

 Coincidir mayúsculas y minúsculas cuando se selecciona, las ventanas resultados de la **búsqueda** solo mostrarán las instancias de la cadena **Buscar** que coincidan tanto con el contenido como con el uso de mayúsculas o minúsculas. Por ejemplo, una búsqueda de "MiObjeto" con la opción **Coincidir mayúsculas y minúsculas** seleccionada, devolverá "MiObjeto" pero no "miobjeto" o "MIOBJETO".

 Solo palabras completas cuando se selecciona, las ventanas resultados de la **búsqueda** solo mostrarán las instancias de la cadena **Buscar** que coincidan con las palabras completas. Por ejemplo, una búsqueda de "MiObjeto" devolverá "MiObjeto" pero no "CMiObjeto" o "MiObjetoC".

 Usar expresiones regulares cuando se activa esta casilla, puede usar las notaciones especiales para definir patrones de texto en los cuadros de texto **Buscar** o **reemplazar con** . Para obtener una lista de estas notaciones, vea [Usar expresiones regulares en Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

 Examine estos tipos de archivo esta lista indica los tipos de archivos que se van a buscar en los directorios **Buscar en** . Si este campo se ha dejado en blanco, se buscará en todos los archivos de los directorios **Buscar en**.

 Seleccione cualquier elemento de la lista para escribir una cadena de búsqueda preconfigurada que buscará archivos de esos tipos determinados.

## <a name="result-options"></a>Opciones de resultados
 Puede expandir o contraer la sección **Opciones de resultados**. Se pueden activar o desactivar las opciones siguientes:

 Ventana Resultados de la búsqueda 1 cuando se selecciona, los resultados de la búsqueda actual reemplazarán el contenido de la ventana Resultados de la búsqueda **1** . Esta ventana se abre automáticamente para mostrar los resultados de la búsqueda. Para abrir esta ventana manualmente, seleccione **Otras ventanas** en el menú **Vista** y pulse **Resultados de la búsqueda 1**.

 Ventana Resultados de la búsqueda 2 cuando se selecciona, los resultados de la búsqueda actual reemplazarán el contenido de la ventana Resultados de la búsqueda **2** . Esta ventana se abre automáticamente para mostrar los resultados de la búsqueda. Para abrir esta ventana manualmente, seleccione **Otras ventanas** en el menú **Vista** y pulse **Resultados de la búsqueda 2**.

 Mostrar nombres de archivo solo cuando se selecciona esta casilla, en las ventanas resultados de la búsqueda se muestran los nombres completos y las rutas de acceso de todos los archivos que contienen la cadena de búsqueda. En cambio, los resultados no incluyen la línea de código donde aparece la cadena. Esta casilla está disponible solo para Buscar en archivos.

 Mantener los archivos modificados abiertos después de reemplazar todo cuando se selecciona, deja abiertos todos los archivos en los que se han realizado reemplazos, de forma que puede deshacerlos o guardarlos. Las restricciones de memoria pueden limitar el número de archivos que pueden seguir abiertos después de una operación de reemplazo.

> [!CAUTION]
> Puede usar **Deshacer** solo en los archivos que siguen abiertos para su edición. Si esta opción no está seleccionada, los archivos que todavía no se han abierto para su edición seguirán cerrados, y ninguna opción **Deshacer** estará disponible en esos archivos.

## <a name="see-also"></a>Vea también
 Buscar [y reemplazar texto](../ide/finding-and-replacing-text.md) [Buscar en archivos](../ide/find-in-files.md) [comandos de Visual Studio](../ide/reference/visual-studio-commands.md)
