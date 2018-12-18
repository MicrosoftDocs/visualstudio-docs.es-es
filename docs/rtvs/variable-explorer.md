---
title: Explorador de variables de R
description: El Explorador de variables de Visual Studio muestra todas las variables en un ámbito determinado en la sesión actual de R.
ms.date: 01/24/2018
ms.prod: visual-studio-dev15
ms.technology: vs-rtvs
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: fbd20c362c407148262d8e1e61e15d22d9cbcf2f
ms.sourcegitcommit: e5a382de633156b85b292f35e3d740f817715d47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/12/2018
ms.locfileid: "38978130"
---
# <a name="variable-explorer"></a>Explorador de variables

En la ventana del **Explorador de variables**, abierta con **Herramientas de R** > **Ventanas** > **Explorador de variables** (o **Ctrl**+**8** si ha usado **Herramientas de R** > **Configuración de ciencia de datos**), se muestran todas las variables en un ámbito determinado de la sesión de R actual. Por ejemplo, si ha abierto el **Explorador de variables** y escribe las líneas siguientes en la [ventana interactiva](interactive-repl-for-r-in-visual-studio.md):

```R
x <- 42
y <- 43
n <- c(1,2,3,5,8,13)
```

Después, la ventana **Explorador de variables** aparece de la manera siguiente:

![Ventana Explorador de variables en Visual Studio](media/variable-explorer-window.png)

Si tiene un marco de datos de R más complejo definido en la sesión, puede navegar por los datos. Por ejemplo, después de ejecutar `cars <- mtcars`, puede navegar por el conjunto de datos expandiendo los diferentes nodos del **Explorador de variables**:

![Vista expandida del Explorador de variables](media/variable-explorer-expanded-results.png)

Para eliminar variables, haga clic con el botón derecho y seleccione **Eliminar** o seleccione la variable y presione la tecla **Eliminar**.

También puede buscar una observación del marco de datos con la búsqueda incremental. Primero, expanda los nodos del marco de datos que quiere buscar, después, escriba los términos de búsqueda en el cuadro de búsqueda.

## <a name="details-table-view"></a>Vista de los detalles (tabla)

Como a menudo los datos son tabulares, puede ver cualquier tipo de datos complejo como una tabla independiente seleccionando el icono de lupa o haciendo clic con el botón derecho y seleccionando **Mostrar detalles**.

![Vista de la tabla Explorador de variables](media/variable-explorer-table-view.png)

Al hacer clic en un encabezado de columna se ordenan los datos por columna (alternando entre ascendente y descendente). Manteniendo presionada la tecla **Mayús** y haciendo clic en las columnas adicionales se agregan también esas columnas a la ordenación. Al hacer clic en una columna sin la tecla **Mayús** se vuelve a una ordenación de columna única.

La secuencia en la que hace clic en los encabezados de columna determina el orden en que se realiza la ordenación. Por ejemplo, al hacer **clic** con **Mayús**+ en la columna **cyl** y, después, hacer **clic** con **Mayús**+ en la columna **mpg** dos veces, se ordena la lista de cilindros ascendentes y millas por galón descendentes:

![Vista de tabla de ordenación de datos en dos columnas.](media/variable-explorer-table-view-sorting.png)

Como el **Explorador de variables** y las vistas de tabla están en ventanas de Visual Studio independientes, puede organizarlas como quiera para el trabajo en paralelo. Vea [Personalizar los diseños de ventana de Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md) para obtener instrucciones generales.

## <a name="open-in-excel-or-other-csv-capable-application"></a>Abrir en Excel (o en otra aplicación compatible con CSV)

Si se quiere una mayor manipulación y análisis, a menudo es útil exportar variables de sesión en CSV. La exportación se realiza con el icono pequeño de Excel (![icono de exportación de Excel](media/variable-explorer-excel-icon.png)) junto a cada nodo del **Explorador de variables** o haciendo clic en el botón derecho sobre un elemento y seleccionando **Abrir en la aplicación de CSV**. Al hacer clic en el icono se escriben los datos en un nuevo archivo CSV de la carpeta *%userprofile%\Documents\RTVS_CSV_Exports* y, después, se inicia ese archivo, que se abre en cualquier aplicación asociada a la extensión *.csv*.

## <a name="scopes"></a>Ámbitos

De manera predeterminada, el **Explorador de variables** se abre en el ámbito global. Puede cambiar a un ámbito de paquete seleccionando un paquete del menú desplegable en la parte superior de la ventana.

![Explorador de variables que muestra un ámbito de paquete](media/variable-explorer-package-scopes.png)

También puede cambiar a un ámbito de función cuando se detiene en un punto de interrupción del depurador (tenga en cuenta que el **Explorador de variables** no cambia automáticamente al ámbito de función del código que se está depurando):

![Explorador de variables que muestra un marco de datos durante la depuración](media/variable-explorer-as-locals-window.png)

El **Explorador de variables** cambia automáticamente el ámbito de función a medida que avanza por el código en el depurador, como mostrar variables locales en una función.

## <a name="import-data-into-variable-explorer"></a>Importar datos en el Explorador de variables

Dos comandos de la barra de herramientas del **Explorador de variables**, que también están disponibles a través del menú **Herramientas de R** > **Datos**, importan conjuntos de datos CSV externos en la sesión de R: **Importar conjunto de datos en la sesión de R a partir de una URL web** y **Importar conjunto de datos en la sesión de R a partir de un archivo de texto**.

Una vez que haya identificado el archivo CSV que se va a importar, Visual Studio muestra un cuadro de diálogo **Importar conjunto de datos** en el que tiene opciones para controlar cómo se analiza ese archivo de datos (es decir, cuál es el separador de campos y cómo controlar las comillas). También puede ver una vista previa del marco de datos importado y del archivo de datos original:

![Cuadro de diálogo Importar conjunto de datos](media/variable-explorer-import-dataset-dialog.png)
