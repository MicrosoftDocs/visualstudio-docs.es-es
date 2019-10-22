---
title: Buscar en archivos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.findreplace.findinfiles
- vs.findinfiles
helpviewer_keywords:
- objects [Visual Studio], finding
- text searches, replacing text
- objects [Visual Studio], searching for
- Find and Replace window, Find in Files tab
- text searches, Find and Replace window
- documents, searching
- files, searching
- Find in Files tab, Find and Replace window
ms.assetid: 989e0737-46d7-4474-8453-fad52a74669d
caps.latest.revision: 45
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5e21d0880813452e37c9e20afdc98321e4b2e3a6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655898"
---
# <a name="find-in-files"></a>Buscar en archivos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Buscar en archivos** permite buscar en un conjunto de archivos especificado. Las coincidencias encontradas y las acciones realizadas se muestran en la ventana **Resultados de la búsqueda** seleccionada en **Opciones de resultados**.

 Puede usar cualquiera de los métodos siguientes para mostrar **Buscar en archivos** en la ventana **Buscar y reemplazar**.

### <a name="to-display-find-in-files"></a>Para mostrar Buscar en archivos

1. En la barra de menús, elija **Editar**, **Buscar y reemplazar**.

2. Elija **Buscar en archivos**.

   Para cancelar una operación de búsqueda, presione Ctrl+Interrumpir.

> [!NOTE]
> La herramienta Buscar y reemplazar no busca en los directorios con el conjunto de atributos `Hidden` o `System`.

## <a name="find-what"></a>Buscar
 Para buscar una nueva cadena de texto o expresión, especifíquela en el cuadro. Para buscar cualquiera de las 20 cadenas que buscó más recientemente, abra la lista y elija la cadena que desea buscar. Pulse el botón **Generador de expresiones** adyacente si quiere usar una o varias expresiones regulares en la cadena de búsqueda. Para obtener más información, vea [Usar expresiones regulares en Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

## <a name="look-in"></a>Buscar en
 La opción elegida en la lista desplegable **Buscar en** determina si **Buscar en archivos** solo busca en los archivos activos actualmente o en todos los archivos almacenados en algunas carpetas. Seleccione un ámbito de búsqueda en la lista o haga clic en el botón **Examinar (...)** para mostrar el cuadro de diálogo **Elegir carpetas de búsqueda** y para especificar su propio conjunto de directorios. También puede escribir una ruta directamente en el cuadro **Buscar en**.

> [!WARNING]
> Con las opciones **Toda la solución** o **Proyecto actual** no se busca en archivos de proyecto y solución. Si desea buscar en archivos de proyecto, elija una carpeta de búsqueda.

> [!NOTE]
> Si la opción **Buscar en** seleccionada conlleva buscar en un archivo que ha desprotegido desde el control de código fuente, solo se busca en la versión de ese archivo que se ha descargado en el equipo local.

## <a name="include-subfolders"></a>Incluir subcarpetas
 Especifica que se buscará en las subcarpetas de la carpeta **Buscar en**.

## <a name="find-options"></a>Opciones de búsqueda
 Puede expandir o contraer la sección **Opciones de búsqueda**. Se pueden activar o desactivar las opciones siguientes:

 Coincidir mayúsculas y minúsculas cuando se selecciona, la búsqueda de **resultados de búsqueda** distinguirá mayúsculas de minúsculas

 Solo palabras completas cuando se selecciona, las ventanas resultados de la **búsqueda** solo devolverán coincidencias con palabras completas.

 Usar expresiones regulares si esta casilla está activada, puede usar notaciones especiales para definir los patrones de texto que deben coincidir en los cuadros de texto **Buscar** o **reemplazar con** . Para obtener una lista de estas notaciones, vea [Usar expresiones regulares en Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

 Examine estos tipos de archivo esta lista indica los tipos de archivos que se van a buscar en los directorios **Buscar en** . Si este campo está en blanco, se buscará en todos los archivos de los directorios **Buscar en**.

 Seleccione cualquier elemento de la lista para escribir una cadena de búsqueda preconfigurada que buscará archivos de esos tipos determinados.

## <a name="result-options"></a>Opciones de resultados
 Puede expandir o contraer la sección **Opciones de resultados**. Se pueden activar o desactivar las opciones siguientes:

 Ventana Resultados de la búsqueda 1 cuando se selecciona, los resultados de la búsqueda actual reemplazarán el contenido de la ventana Resultados de la búsqueda **1** . Esta ventana se abre automáticamente para mostrar los resultados de la búsqueda. Para abrir esta ventana manualmente, seleccione **Otras ventanas** en el menú **Vista** y pulse **Resultados de la búsqueda 1**.

 Ventana Resultados de la búsqueda 2 cuando se selecciona, los resultados de la búsqueda actual reemplazarán el contenido de la ventana Resultados de la búsqueda **2** . Esta ventana se abre automáticamente para mostrar los resultados de la búsqueda. Para abrir esta ventana manualmente, seleccione **Otras ventanas** en el menú **Vista** y pulse **Resultados de la búsqueda 2**.

 Mostrar nombres de archivo solo muestra una lista de archivos que contienen coincidencias de búsqueda en lugar de mostrar las coincidencias de la búsqueda.

 Anexar resultados anexa los resultados de la búsqueda a los resultados de búsqueda anteriores.

## <a name="see-also"></a>Vea también
 [Buscar y reemplazar texto](../ide/finding-and-replacing-text.md) [reemplazar en archivos](../ide/replace-in-files.md) [comandos de Visual Studio](../ide/reference/visual-studio-commands.md)
