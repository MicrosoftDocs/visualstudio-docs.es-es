---
title: Procedimiento Depurar código fuente de .NET Framework | Microsoft Docs
ms.date: 11/19/2018
ms.topic: conceptual
helpviewer_keywords:
- debugging, .NET Framework source
ms.assetid: fc12e472-ac6a-4e77-8e22-a769e13a03b8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 25f40b0528b794863aabdb13ed9785d2b0c551b8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62894279"
---
# <a name="how-to-debug-net-framework-source"></a>Procedimiento Depurar código fuente de .NET Framework

Para depurar código fuente de .NET Framework, debe:

- Habilitar ejecución paso a paso en el código fuente de .NET Framework.

- Tener acceso a los símbolos de depuración para el código.

  Puede descargar los símbolos de depuración inmediatamente o establecer las opciones para una descarga posterior. Si los símbolos no descarga inmediatamente, descargará la próxima vez que se inicie la depuración de la aplicación. Durante la depuración, también puede usar el **módulos** o **pila de llamadas** windows para descargar y cargar los símbolos.

### <a name="to-enable-stepping-into-net-framework-source"></a>Para habilitar la ejecución paso a paso en el código fuente de .NET Framework

1. En **herramientas** (o **depurar**) > **opciones** > **depuración** > **General**, seleccione **fuente de .NET Framework de habilitar ejecución paso a paso**.

   - Si tenía habilitada la opción Sólo mi código , un cuadro de diálogo de advertencia le indicará que dicha opción se ha deshabilitado. Seleccione **Aceptar**.

   - Si no tenía una caché de símbolos local establecido, un cuadro de diálogo de advertencia indica que se ha establecido una caché de símbolos predeterminado. Seleccione **Aceptar**.

1. Seleccione **Aceptar** para cerrar el **opciones** cuadro de diálogo.

### <a name="to-set-or-change-symbol-source-locations-and-loading-behavior"></a>Para establecer o cambiar las ubicaciones de origen de símbolos y el comportamiento de carga

1. Seleccione el **símbolos** categoría **herramientas** (o **depurar**) > **opciones** > **dedepuración**.

1. En el **símbolos** página, en **ubicaciones de archivo (.pdb) de símbolos**, seleccione **servidores de símbolos de Microsoft** a los símbolos de acceso de los servidores de símbolos públicos de Microsoft. Seleccione los botones de barra de herramientas para agregar otras ubicaciones de símbolos y cambiar el orden de carga.

1. Para cambiar la memoria caché de símbolos locales, editar o buscar una ubicación diferente en **almacenar en caché los símbolos de este directorio**.

1. Para descargar los símbolos inmediatamente, seleccione **cargar todos los símbolos**. Este botón está disponible solo durante la depuración.

   Si no descargar ahora los símbolos, se deberá descargar la próxima vez que se inicie la depuración.

1. Seleccione **Aceptar** para cerrar el **opciones** cuadro de diálogo.

### <a name="to-load-symbols-from-the-modules-or-call-stack-windows"></a>Para cargar símbolos desde los módulos o la pila de llamadas de windows

1. Durante la depuración, abra la ventana seleccionando **depurar** > **Windows** > **módulos** (o presione **Ctrl + Alt + U**) o **depurar** > **Windows** > **pila de llamadas** (**Ctrl + Alt + C**).

1. Haga clic en un módulo para el que no se han cargado los símbolos. En el **módulos** ventana, estado de carga de símbolos está en el **símbolos estado** columna. En el **pila de llamadas** ventana, el estado está en el **estado marco** columna y el marco está atenuado.

   - Seleccione **cargar símbolos** en el menú para buscar y cargar los archivos de símbolos desde una carpeta en el equipo.

   - Seleccione **información de carga de símbolos** para mostrar las ubicaciones que el depurador busca los símbolos.

   - Seleccione **configuración de símbolos** para abrir el **símbolos** página. En el **símbolos** página, en **ubicaciones de archivo (.pdb) de símbolos**, seleccione **servidores de símbolos de Microsoft** a los símbolos de acceso de los servidores de símbolos públicos de Microsoft. Seleccione los botones de barra de herramientas para agregar otras ubicaciones de símbolos y cambiar el orden de carga. Seleccione **Aceptar** para cerrar el cuadro de diálogo.

### <a name="see-also"></a>Vea también
- [Depurar código administrado](../debugger/debugging-managed-code.md)
- [Especificación de archivos de código fuente y símbolos (.pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)