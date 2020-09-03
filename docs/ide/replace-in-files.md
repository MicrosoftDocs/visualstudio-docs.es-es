---
title: Búsqueda y reemplazo en archivos
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.findreplace.replaceinfiles
- vs.replaceinfiles
helpviewer_keywords:
- text searches, replacing text
- find and replace
- replace in files
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dddd55714e53516ba1ccd8a11c99761a4db7136a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "75585631"
---
# <a name="replace-in-files"></a>Reemplazar en archivos

**Reemplazar en archivos** le permite buscar el código de un conjunto de archivos especificado para una cadena o expresión, y cambiar algunas o todas las coincidencias que ha detectado. Las coincidencias encontradas y las acciones realizadas se muestran en la ventana **Resultados de la búsqueda** seleccionada en **Opciones de resultados**.

> [!NOTE]
> Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la **Ayuda**, en función de los valores de configuración o de edición activos. Para cambiar la configuración, por ejemplo, **General** o **Visual C++**, elija **Herramientas** > **Importar y exportar configuraciones** y, después, **Restablecer todas las configuraciones**.

Puede usar cualquiera de los métodos siguientes para mostrar **Reemplazar en archivos** en la ventana **Buscar y reemplazar**.

## <a name="to-display-replace-in-files"></a>Para mostrar Reemplazar en archivos

1. En el menú **Edición**, expanda **Buscar y reemplazar**.

2. Pulse **Reemplazar en archivos**.

   o

   Si la ventana **Buscar y reemplazar** ya está abierta, en la barra de herramientas, pulse **Reemplazar en archivos**.

## <a name="find-what"></a>Buscar

Para buscar una nueva cadena de texto o expresión, especifíquela en el cuadro. Para encontrar cualquiera de las últimas 20 cadenas que haya buscado, abra la lista desplegable y elija la cadena en cuestión. Pulse el botón **Generador de expresiones** adyacente si quiere usar una o varias expresiones regulares en la cadena de búsqueda. Para obtener más información, vea [Usar expresiones regulares en Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

> [!NOTE]
> El botón **Generador de expresiones** solo estará habilitado si ha seleccionado **Usar expresiones regulares** en **Opciones de búsqueda**.

## <a name="replace-with"></a>Reemplazar por

Para reemplazar instancias de la cadena en el cuadro **Buscar** por otra cadena, escriba la cadena de reemplazo en el cuadro **Reemplazar por**. Para eliminar instancias de la cadena en el cuadro **Buscar**, deje este campo en blanco. Abra la lista para mostrar las 20 cadenas que ha buscado más recientemente. Pulse el botón **Generador de expresiones** adyacente si quiere usar una o varias expresiones regulares en la cadena de reemplazo. Para obtener más información, vea [Usar expresiones regulares en Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

## <a name="look-in"></a>Buscar en

La opción elegida en la lista desplegable **Buscar en** determina si **Reemplazar en archivos** busca solo en los archivos actualmente activos o busca en todos los archivos almacenados en algunas carpetas. Seleccione un ámbito de búsqueda en la lista, escriba una ruta de carpeta o haga clic en el botón **Examinar (...)** para mostrar el cuadro de diálogo **Elegir carpetas de búsqueda** y seleccionar un conjunto de carpetas para buscar. También puede escribir una ruta directamente en el cuadro **Buscar en**.

> [!NOTE]
> Si la opción **Buscar en** seleccionada conlleva buscar en un archivo que ha desprotegido desde el control de código fuente, solo se busca en la versión de ese archivo que se ha descargado en el equipo local.

## <a name="find-options"></a>Opciones de búsqueda

Puede expandir o contraer la sección **Opciones de búsqueda**. Se pueden activar o desactivar las opciones siguientes:

**Coincidir mayúsculas y minúsculas**

Cuando está seleccionada, las ventanas **Resultados de búsqueda** solo mostrarán instancias de la cadena **Buscar** que coinciden en contenido y en mayúsculas y minúsculas. Por ejemplo, una búsqueda de "MiObjeto" con la opción **Coincidir mayúsculas y minúsculas** seleccionada, devolverá "MiObjeto" pero no "miobjeto" o "MIOBJETO".

**Solo palabras completas**

Cuando está seleccionada, las ventanas **Resultados de búsqueda** solo mostrarán instancias de la cadena **Buscar** que coinciden en palabras completas. Por ejemplo, una búsqueda de "MiObjeto" devolverá "MiObjeto" pero no "CMiObjeto" o "MiObjetoC".

**Uso de expresiones regulares**

Cuando esta casilla está seleccionada, puede usar las notaciones especiales para definir los patrones de texto en los cuadros de texto **Buscar** o **Reemplazar con**. Para obtener una lista de estas notaciones, vea [Usar expresiones regulares en Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

**Buscar en estos tipos de archivo**

Esta lista indica los tipos de archivos en los que se va a buscar en los directorios **Buscar en**. Si este campo se ha dejado en blanco, se buscará en todos los archivos de los directorios **Buscar en**. Seleccione cualquier elemento de la lista para escribir una cadena de búsqueda preconfigurada que buscará archivos de esos tipos determinados.

## <a name="result-options"></a>Opciones de resultados

Puede expandir o contraer la sección **Opciones de resultados**. Se pueden activar o desactivar las opciones siguientes:

Ventana **Resultados de la búsqueda 1**

Cuando se selecciona, los resultados de la búsqueda actual reemplazarán el contenido de la ventana **Resultados de la búsqueda 1**. Esta ventana se abre automáticamente para mostrar los resultados de la búsqueda. Para abrir esta ventana manualmente, seleccione **Otras ventanas** en el menú **Vista** y pulse **Resultados de la búsqueda 1**.

Ventana **Resultados de la búsqueda 2**

Cuando se selecciona, los resultados de la búsqueda actual reemplazarán el contenido de la ventana **Resultados de la búsqueda 2**. Esta ventana se abre automáticamente para mostrar los resultados de la búsqueda. Para abrir esta ventana manualmente, seleccione **Otras ventanas** en el menú **Vista** y pulse **Resultados de la búsqueda 2**.

**Mostrar solo nombres de archivo**

Cuando esta casilla está seleccionada, en las ventanas **Resultados de la búsqueda** se muestran los nombres completos y las rutas de acceso de todos los archivos que contienen la cadena de búsqueda. En cambio, los resultados no incluyen la línea de código donde aparece la cadena. Esta casilla solo está disponible para **Buscar en archivos**.

**Mantener los archivos modificados abiertos después de Reemplazar todo**

Cuando se selecciona, deja abiertos todos los archivos en los que se han realizado reemplazos, de forma que puede deshacerlos o cambiarlos. Las restricciones de memoria pueden limitar el número de archivos que pueden permanecer abiertos después de una operación de reemplazo.

> [!CAUTION]
> Puede utilizar **Deshacer** solo en los archivos que permanecen abiertos para edición. Si no se selecciona esta opción, los archivos que no estén abiertos para edición permanecerán cerrados y no estará disponible la opción **Deshacer** para ellos.

## <a name="see-also"></a>Consulte también

- [Buscar y reemplazar texto](../ide/finding-and-replacing-text.md)
- [Buscar en archivos](../ide/find-in-files.md)
- [Comandos de Visual Studio](../ide/reference/visual-studio-commands.md)
