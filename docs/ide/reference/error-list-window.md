---
title: Lista de errores (ventana)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ErrorList
helpviewer_keywords:
- Task List
- build errors
- Error List window
- errors [Visual Studio], Error List window
ms.assetid: b7f6d45a-733b-4ad8-bc2f-737a37509e56
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5fe70a8c7daeac86ea3a354f81d8462ca7f4e451
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55933982"
---
# <a name="error-list-window"></a>Lista de errores (ventana)

> [!NOTE]
> La **Lista de errores** muestra información sobre un mensaje de error determinado. Puede copiar el número o el texto de la cadena del error de la ventana **Salida**. Para mostrar la ventana **Salida**, presione **Ctrl**+**Alt**+**O**. Vea [Resultados (ventana)](../../ide/reference/output-window.md).

La ventana **Lista de errores** permite realizar las siguientes tareas:

-   Mostrar los errores, las advertencias y los mensajes que se generan mientras escribe el código.

-   Buscar errores de sintaxis detectados por IntelliSense.

-   Buscar errores de implementación, ciertos errores de análisis estático y errores detectados mientras se aplican directivas de Enterprise Templates.

-   Hacer doble clic en la entrada de cualquier mensaje de error para abrir el archivo donde se produce el problema y desplazarse a la ubicación del error.

-   Filtrar las entradas que se muestran y las columnas de información que aparecen para cada entrada.

-   Buscar términos específicos y delimitar la búsqueda solo al proyecto o documento actual.

Para mostrar la **Lista de errores**, elija **Ver** > **Lista de errores** o bien presione **Ctrl**+**\\**+**E**.

Puede seleccionar las pestañas **Errores**, **Advertencias** y **Mensajes** para ver diferentes niveles de información.

Para ordenar la lista, haga clic en cualquier encabezado de columna. Para ordenar de nuevo por otra columna, mantenga presionada la tecla **Mayús** y haga clic en otro encabezado de columna. Para seleccionar las columnas que se muestran y las que están ocultas, seleccione **Mostrar columnas** en el menú contextual. Si desea cambiar el orden en el que se muestran las columnas, arrastre cualquier encabezado de columna hacia la izquierda o la derecha.

## <a name="error-list-filters"></a>Filtros de la lista de errores

Hay dos tipos de filtro en dos listas desplegables, una en el lado derecho de la barra de herramientas y otra a la izquierda de la barra de herramientas. La lista desplegable del lado izquierdo de la barra de herramientas especifica el conjunto de archivos de código que se va a usar (**Toda la solución**, **Documentos abiertos**, **Proyecto actual** o **Documento actual**).

Puede limitar el ámbito de búsqueda para analizar y actuar en grupos de errores. Por ejemplo, puede que desee centrarse en los errores más importantes que están impidiendo que un proyecto se compile. Entre las opciones para delimitar el ámbito se incluyen las siguientes:

1.  **Documentos abiertos**: Muestra los errores, las advertencias y los mensajes de los documentos abiertos.

2.  **Proyecto actual**: Muestra los errores, las advertencias y los mensajes del proyecto del documento seleccionado actualmente en el **Editor** o del proyecto seleccionado en **Explorador de soluciones**.

    > [!NOTE]
    > La lista filtrada de errores, advertencias y mensajes cambia si el proyecto del documento seleccionado actualmente es diferente al proyecto seleccionado en el **Explorador de soluciones**.

3.  **Documento actual**: Muestra los errores, las advertencias y los mensajes del documento seleccionado actualmente en **Editor** o **Explorador de soluciones**.

Si se aplica un filtro actualmente al resultado de la búsqueda, el nombre del filtro aparece en la barra de título de **Lista de errores**. Los botones **Errores**, **Advertencias** y **Mensajes** muestran el número de elementos filtrados mostrados junto con el número total de elementos. Por ejemplo, los botones muestran "x de y errores". Si no se aplica ningún filtro, en la barra de título solo aparece "Lista de errores".

La lista que se muestra en el lado derecho de la barra de herramientas especifica si se muestran los errores desde la compilación (los errores resultantes de una operación de compilación), desde IntelliSense (los errores detectados antes de ejecutar una compilación) o desde ambos.

## <a name="search"></a>Buscar

Use el cuadro de texto **Lista de errores de búsqueda** en el lado derecho de la barra de herramientas **Lista de errores** para buscar errores específicos en la lista de errores. Puede buscar en cualquier columna visible de la lista de errores. Los resultados de la búsqueda siempre se ordenan en función de la columna que tenga prioridad de ordenación en lugar de la consulta o el filtro aplicado. Si presiona la tecla **Esc** mientras el foco está en la **Lista de errores**, se borra el término de búsqueda y los resultados filtrados de la búsqueda. También puede hacer clic en la **X** que se muestra en el lado derecho del cuadro de texto para borrarlos.

## <a name="save"></a>Guardar

Puede copiar la lista de errores y guardarla en un archivo. Seleccione los errores que quiere copiar, haga clic con el botón derecho en la selección y, después, seleccione **Copiar** en el menú contextual. Después puede pegar los errores en un archivo. Si pega los errores en una hoja de cálculo de Excel, los campos aparecen como columnas diferentes.

## <a name="ui-element-list"></a>Lista de elementos de la interfaz de usuario

Gravedad

Muestra los diferentes tipos de entrada de la **Lista de errores** (**Error**, **Mensaje**, **Advertencia**, **Advertencia (activa)** y **Advertencia (inactiva)**.

Código

Muestra el código del error.

Descripción

Muestra el texto de la entrada.

Proyecto

Muestra el nombre del proyecto actual.

Archivo

Muestra el nombre del archivo.

Línea

Muestra la línea en la que se produce el problema.