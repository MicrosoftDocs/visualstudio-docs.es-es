---
title: Buscar en archivos
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e1470868e207687a7b35f46724b80b0da0a0e71c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31946564"
---
# <a name="find-in-files"></a>Buscar en archivos

**Buscar en archivos** permite buscar en un conjunto de archivos especificado. Las coincidencias encontradas y las acciones realizadas se muestran en la ventana **Resultados de la búsqueda** seleccionada en **Opciones de resultados**.

Puede usar cualquiera de los métodos siguientes para mostrar **Buscar en archivos** en la ventana **Buscar y reemplazar**.

## <a name="to-display-find-in-files"></a>Para mostrar Buscar en archivos

1. En la barra de menús, elija **Editar** > **Buscar y reemplazar**.

1. Elija **Buscar en archivos**.

Para cancelar una operación de búsqueda, presione **CTRL** + **Interrumpir**.

> [!NOTE]
> La herramienta Buscar y reemplazar no busca en los directorios que tengan los atributos `Hidden` o `System`.

## <a name="find-what"></a>Buscar

Para buscar una nueva cadena de texto o expresión, especifíquela en el cuadro. Para encontrar cualquiera de las últimas 20 cadenas que haya buscado, abra la lista desplegable y elija la cadena en cuestión. Pulse el botón **Generador de expresiones** adyacente si quiere usar una o varias expresiones regulares en la cadena de búsqueda. Para obtener más información, vea [Usar expresiones regulares en Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

> [!NOTE]
> El botón **Generador de expresiones** solo estará habilitado si ha seleccionado **Usar expresiones regulares** en **Opciones de búsqueda**.

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

**Coincidir mayúsculas y minúsculas**

Cuando se selecciona, la búsqueda **Resultados de la búsqueda** distinguirá entre mayúsculas y minúsculas

**Solo palabras completas**

Cuando se selecciona, las ventanas**Resultados de la búsqueda** solo devolverán coincidencias de palabras completas.

**Uso de expresiones regulares**

Si se selecciona esta casilla, puede usar las notaciones especiales para definir los patrones de texto que deben coincidir en los cuadros de texto **Buscar** o **Reemplazar con**. Para obtener una lista de estas notaciones, vea [Usar expresiones regulares en Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

**Buscar en estos tipos de archivo**

Esta lista indica los tipos de archivos en los que se va a buscar en los directorios **Buscar en**. Si este campo está en blanco, se buscará en todos los archivos de los directorios **Buscar en**.

Seleccione cualquier elemento de la lista para escribir una cadena de búsqueda preconfigurada que buscará archivos de esos tipos determinados.

## <a name="result-options"></a>Opciones de resultados

Puede expandir o contraer la sección **Opciones de resultados**. Se pueden activar o desactivar las opciones siguientes:

**Ventana Resultados de la búsqueda 1**

Cuando se selecciona, los resultados de la búsqueda actual reemplazarán el contenido de la ventana **Resultados de la búsqueda 1**. Esta ventana se abre automáticamente para mostrar los resultados de la búsqueda. Para abrir esta ventana manualmente, seleccione **Otras ventanas** en el menú **Vista** y pulse **Resultados de la búsqueda 1**.

**Ventana Resultados de la búsqueda 2**

Cuando se selecciona, los resultados de la búsqueda actual reemplazarán el contenido de la ventana **Resultados de la búsqueda 2**. Esta ventana se abre automáticamente para mostrar los resultados de la búsqueda. Para abrir esta ventana manualmente, seleccione **Otras ventanas** en el menú **Vista** y pulse **Resultados de la búsqueda 2**.

**Mostrar solo nombres de archivo**

Muestra una lista de archivos que contienen coincidencias con la búsqueda, en lugar de mostrar las propias coincidencias.

**Anexar resultados**

Agrega los resultados de la búsqueda a los resultados de la búsqueda anteriores.

## <a name="see-also"></a>Vea también

- [Buscar y reemplazar texto](../ide/finding-and-replacing-text.md)
- [Reemplazar en archivos](../ide/replace-in-files.md)
- [Comandos de Visual Studio](../ide/reference/visual-studio-commands.md)