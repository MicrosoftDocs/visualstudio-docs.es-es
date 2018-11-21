---
title: Ver los archivos DLL y ejecutables en la ventana módulos | Microsoft Docs
ms.custom: H1Hack27Feb2017
ms.date: 11/04/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.modules
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, Modules window
- Modules window
- executable files, displaying while debugging
- debugging [Visual Studio], displaying modules
- DLLs, displaying while debugging
- modules, displaying
ms.assetid: d840fdca-b035-4452-b652-72580c831896
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 33a09fe01157e0e3f5493568437c1499f2831bdb
ms.sourcegitcommit: a7de99f36e9ead7ea9e9bac23c88d05ddfc38b00
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2018
ms.locfileid: "52257295"
---
# <a name="view-dlls-and-executables-in-the-modules-window-c-c-visual-basic-f"></a>Ver los archivos DLL y ejecutables en la ventana Módulos (C#, C++, Visual Basic, F#)
 
Durante la depuración de Visual Studio, el **módulos** ventana enumera y muestra información acerca de los archivos DLL y ejecutables (*.exe* archivos) utiliza su aplicación. 

> [!NOTE]
> La ventana módulos no está disponible para la depuración de script o SQL. 
  
## <a name="use-the-modules-window"></a>Utilice la ventana módulos

Para abrir la ventana módulos, durante la depuración, seleccione **depurar** > **Windows** > **módulos**. 
  
De forma predeterminada, el **módulos** ventana ordena los módulos por orden de carga. Para ordenar por cualquier columna de la ventana, seleccione el encabezado en la parte superior de la columna.  
  
## <a name="load-symbols"></a>Cargar símbolos  

El **estado del símbolo** columna en el **módulos** ventana muestra qué módulos tienen cargados los símbolos de depuración. Si el estado es **se omitió la carga de símbolos**, **no se puede encontrar o abrir el archivo PDB**, o **carga deshabilitada por el parámetro incluir/excluir**, puede cargar símbolos manualmente. Para obtener más información sobre la carga y uso de símbolos, vea [especificar archivos de código fuente y símbolos (.pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

**Para cargar símbolos manualmente:**  

1. En el **módulos** (ventana), con el botón secundario el módulo para los símbolos que no ha cargado. 
   
   - Seleccione **cargar información de símbolos** para obtener más información acerca de por qué no se ha cargado los símbolos. 
   
   - Seleccione **cargar símbolos** para cargar los símbolos manualmente.  
   
1. Si no se cargan los símbolos, seleccione **configuración de símbolos** para abrir el **opciones** cuadro de diálogo y especificar o cambiar las ubicaciones de carga de símbolos. 
   
   Puede descargar los símbolos de los servidores de símbolos públicos de Microsoft u otros servidores o cargar símbolos desde una carpeta en el equipo. Para obtener más información, consulte [especificar ubicaciones de símbolos y el comportamiento de carga](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Specify_symbol_locations_and_loading_behavior).   

**Para cambiar la configuración del comportamiento de carga de símbolos:**  

1. En el **módulos** ventana, haga clic en cualquier módulo.  
   
1. Seleccione **Lores**.  
  
1. Seleccione **cargar todos los símbolos**, o seleccione los módulos que desea incluir o excluir.  
  
1. Seleccione **Aceptar**. Los cambios surten efecto en la siguiente sesión de depuración.  
  
**Para cambiar el comportamiento de un módulo específico de carga de símbolos:**  

1.  En el **módulos** ventana, haga clic en el módulo.  

1.  En el menú contextual, seleccione o deseleccione **siempre carga automáticamente**. Los cambios surten efecto en la siguiente sesión de depuración.  
  
## <a name="see-also"></a>Vea también  
 [Interrumpir la ejecución](/previous-versions/visualstudio/visual-studio-2010/7z9se2d8(v=vs.100))   
 [Visualización de datos en el depurador](../debugger/viewing-data-in-the-debugger.md)   
 [Especificar archivos de código fuente y símbolos (.pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)