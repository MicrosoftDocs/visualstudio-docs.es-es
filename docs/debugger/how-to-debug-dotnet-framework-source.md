---
title: Depuración de código fuente de .NET Framework | Microsoft Docs
ms.date: 11/19/2018
ms.topic: how-to
helpviewer_keywords:
- debugging, .NET Framework source
ms.assetid: fc12e472-ac6a-4e77-8e22-a769e13a03b8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: f054564ff36c538b18525ec9d8adf9b6f3d060b9
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852131"
---
# <a name="how-to-debug-net-framework-source"></a>Procedimiento Depurar código fuente de .NET Framework

Para depurar el código fuente de .NET Framework, debe:

- Habilitar la ejecución paso a paso de código fuente de .NET Framework.

- Tener acceso a los símbolos de depuración del código.

  Puede optar por descargar símbolos de depuración inmediatamente o establecer opciones para su descarga posterior. Si no descarga los símbolos inmediatamente, se descargarán la próxima vez que empiece a depurar la aplicación. Durante la depuración, también puede usar las ventanas **Módulos** o **Pila de llamadas** para descargar y cargar símbolos.

### <a name="to-enable-stepping-into-net-framework-source"></a>Para habilitar la ejecución paso a paso de código fuente de .NET Framework

1. En **Herramientas** (o **Depurar**) > **Opciones** > **Depuración** > **General**, seleccione **Habilitar ejecución paso a paso de código fuente de .NET Framework**.

   - Si tenía habilitada la opción Sólo mi código , un cuadro de diálogo de advertencia le indicará que dicha opción se ha deshabilitado. Seleccione **Aceptar**.

   - Si no tenía ninguna caché de símbolos local establecida, otro cuadro de diálogo de advertencia le indicará que se ha establecido una caché de símbolos predeterminada. Seleccione **Aceptar**.

1. Seleccione **Aceptar** para cerrar el diálogo **Opciones**.

### <a name="to-set-or-change-symbol-source-locations-and-loading-behavior"></a>Para establecer o cambiar las ubicaciones de origen y el comportamiento de carga de los símbolos

1. Seleccione la categoría **Símbolos** en **Herramientas** (o **Depuración**) > **Opciones** > **Depurar**.

1. En la página **Símbolos**, en **Ubicaciones de archivos de símbolos (.pdb)** , seleccione **Servidores de símbolos de Microsoft** para obtener acceso a los símbolos de los servidores de símbolos públicos de Microsoft. Seleccione los botones de la barra de herramientas para agregar otras ubicaciones de símbolos y cambiar el orden de carga.

1. Para cambiar la memoria caché de símbolos local, edite o busque otra ubicación en **Almacenar en caché los símbolos de este directorio**.

1. Para descargar símbolos inmediatamente, seleccione **Cargar todos los símbolos**. Este botón solo está disponible durante la depuración.

   Si no descarga los símbolos ahora, se descargarán la próxima vez que inicie la depuración.

1. Seleccione **Aceptar** para cerrar el diálogo **Opciones**.

### <a name="to-load-symbols-from-the-modules-or-call-stack-windows"></a>Para cargar símbolos desde las ventanas Módulos o Pila de llamadas

1. Durante la depuración, abra la ventana; para ello, seleccione **Depurar** > **Ventanas** > **Módulos** (o presione **Ctrl + Alt + U**) o **Depurar** > **Ventanas** > **Pila de llamadas** (**Ctrl + Alt + C**).

1. Haga clic con el botón secundario en un módulo del que no se han cargado los símbolos. En la ventana **Módulos**, el estado de carga de símbolos está en la columna **Estado de los símbolos**. En la ventana **Pila de llamadas**, el estado se encuentra en la columna **Estado de marco** y el marco está atenuado.

   - Seleccione **Cargar símbolos** en el menú para buscar y cargar archivos de símbolos desde una carpeta de su equipo.

   - Seleccione **Información de carga de símbolos** para mostrar las ubicaciones en las que el depurador ha buscado los símbolos.

   - Seleccione **Configuración de símbolos** para abrir la página **Símbolos**. En la página **Símbolos**, en **Ubicaciones de archivos de símbolos (.pdb)** , seleccione **Servidores de símbolos de Microsoft** para obtener acceso a los símbolos de los servidores de símbolos públicos de Microsoft. Seleccione los botones de la barra de herramientas para agregar otras ubicaciones de símbolos y cambiar el orden de carga. Seleccione **Aceptar** para cerrar el cuadro de diálogo.

### <a name="see-also"></a>Vea también
- [Depurar código administrado](../debugger/debugging-managed-code.md)
- [Especificación de archivos de código fuente y símbolos (.pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)