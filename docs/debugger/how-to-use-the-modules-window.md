---
title: Ver los archivos DLL y ejecutables en el depurador | Documentos de Microsoft
ms.custom: H1Hack27Feb2017
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.modules
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
caps.latest.revision: "36"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 772c252265e15c3c928fbcc47c756ceafd9e1362
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="view-dlls-and-executables-using-the-modules-window-in-the-visual-studio-debugger"></a>Ver los archivos DLL y ejecutables mediante la ventana módulos en el depurador de Visual Studio
 
El **módulos** ventana enumera los archivos DLL y los archivos ejecutables (EXE) utilizados por el programa y se muestran la información pertinente para cada uno de ellos. 

> [!NOTE]
>  Esta característica no está disponible para la depuración de SQL o de script. 
  
### <a name="to-display-the-modules-window"></a>Para mostrar la ventana módulos  
  
-   Durante la depuración, seleccione **Depurar > Windows** y, a continuación, haga clic en **módulos**.  
  
     De forma predeterminada, el **módulos** ventana ordena los módulos por orden de carga. No obstante, puede ordenarlos por columnas.  
  
### <a name="to-sort-by-any-column"></a>Para ordenarlos por columnas  
  
-   Haga clic en el botón situado en la parte superior de la columna.  
  
     Puede cargar los símbolos o especificar una ruta de acceso de símbolos de la **módulos** ventana mediante el menú contextual.  
  
## <a name="loading-symbols"></a>Cargar Símbolos  
 En el **módulos** ventana, puede ver qué módulos tienen cargados los símbolos de depuración. Esta información aparece en el **estado del símbolo** columna. Si el estado dice **loadingCannot omitidos encontrar o abrir el archivo PDB**, o **carga deshabilitada por la configuración de inclusión o exclusión**, puede dirigir el depurador para descargar los símbolos de los símbolos públicos de Microsoft servidores o para cargar símbolos desde un directorio de símbolos en el equipo. Para obtener más información, vea [especificar símbolos (.pdb) y archivos de código fuente](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)  
  
#### <a name="to-load-symbols-manually"></a>Para cargar símbolos manualmente  
  
1.  En el **módulos** ventana, menú contextual de un módulo para el que no se cargaron símbolos.  
  
2.  Seleccione **cargar símbolos desde** y, a continuación, haga clic en **servidores de símbolos de Microsoft** o **ruta de acceso de símbolos**.  
  
#### <a name="to-change-symbol-load-settings"></a>Para cambiar la configuración de carga de símbolos  
  
1.  En el **módulos** ventana, haga clic en cualquier módulo.  
  
2.  Haga clic en **configuración de símbolos**.  
  
     Ahora puede cambiar la configuración de carga de símbolos, como se describe en [especificar ubicaciones de símbolos y el comportamiento de carga](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Specify_symbol_locations_and_loading_behavior). Los cambios no surten efecto hasta que se reinicie la sesión de depuración.  
  
#### <a name="to-change-symbol-load-behavior-for-a-specific-module"></a>Para cambiar el comportamiento de carga de símbolos para un módulo específico  
  
1.  En el **módulos** ventana, haga clic en el módulo.  
  
2.  Seleccione **configuración de carga de símbolos automática** y, a continuación, haga clic en **cargar siempre manualmente** o **predeterminado**. Los cambios no surten efecto hasta que se reinicie la sesión de depuración.  
  
## <a name="see-also"></a>Vea también  
 [Interrumpir la ejecución](http://msdn.microsoft.com/en-us/30fc4643-f337-4651-b1ff-f2de2c098d40)   
 [Ver los datos en el depurador](../debugger/viewing-data-in-the-debugger.md)   
 [Especificar los símbolos (.pdb) y archivos de código fuente](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)