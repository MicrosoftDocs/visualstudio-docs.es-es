---
title: Ver los archivos DLL y ejecutables en el depurador | Microsoft Docs
ms.custom: H1Hack27Feb2017
ms.date: 11/04/2016
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
ms.openlocfilehash: f582c435239c83503b179d6bb5e142936a41cb4b
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2018
ms.locfileid: "44279016"
---
# <a name="view-dlls-and-executables-using-the-modules-window-in-the-visual-studio-debugger"></a>Ver los archivos DLL y ejecutables mediante la ventana módulos en el depurador de Visual Studio
 
El **módulos** ventana enumera los archivos DLL y ejecutables (EXE) que son utilizados por el programa y muestran información pertinente para cada uno. 

> [!NOTE]
>  Esta característica no está disponible para la depuración de SQL o de script. 
  
### <a name="to-display-the-modules-window"></a>Para mostrar la ventana módulos  
  
-   Durante la depuración, seleccione **Depurar > Windows** y, a continuación, haga clic en **módulos**.  
  
     De forma predeterminada, el **módulos** ventana ordena los módulos por orden de carga. No obstante, puede ordenarlos por columnas.  
  
### <a name="to-sort-by-any-column"></a>Para ordenarlos por columnas  
  
-   Haga clic en el botón situado en la parte superior de la columna.  
  
     Puede cargar los símbolos o especificar una ruta de acceso de símbolos desde la **módulos** ventana mediante el menú contextual.  
  
## <a name="loading-symbols"></a>Cargar Símbolos  
 En el **módulos** ventana, puede ver qué módulos tienen cargados los símbolos de depuración. Esta información aparece en el **estado del símbolo** columna. Si el estado dice **loadingCannot omitida encontrar o abrir el archivo PDB**, o **carga deshabilitada por el parámetro incluir/excluir**, puede dirigir el depurador para descargar símbolos de los símbolos públicos de Microsoft los servidores o para cargar símbolos desde un directorio de símbolos en el equipo. Para obtener más información, consulte [especificar símbolos (.pdb) y archivos de origen](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)  
  
#### <a name="to-load-symbols-manually"></a>Para cargar símbolos manualmente  
  
1.  En el **módulos** ventana, haga un módulo para el que no han cargado los símbolos.  
  
2.  Seleccione **cargar símbolos desde** y, a continuación, haga clic en **servidores de símbolos de Microsoft** o **ruta de acceso de símbolos**.  
  
#### <a name="to-change-symbol-load-settings"></a>Para cambiar la configuración de carga de símbolos  
  
1.  En el **módulos** ventana, haga clic en cualquier módulo.  
  
2.  Haga clic en **Lores**.  
  
     Ahora puede cambiar la configuración de carga de símbolos, como se describe en [especificar ubicaciones de símbolos y el comportamiento de carga](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Specify_symbol_locations_and_loading_behavior). Los cambios no surten efecto hasta que se reinicie la sesión de depuración.  
  
#### <a name="to-change-symbol-load-behavior-for-a-specific-module"></a>Para cambiar el comportamiento de carga de símbolos para un módulo específico  
  
1.  En el **módulos** ventana, haga clic en el módulo.  
  
2.  Seleccione **configuración de carga de símbolos automática** y, a continuación, haga clic en **cargar siempre manualmente** o **predeterminado**. Los cambios no surten efecto hasta que se reinicie la sesión de depuración.  
  
## <a name="see-also"></a>Vea también  
 [Interrumpir la ejecución](/previous-versions/visualstudio/visual-studio-2010/7z9se2d8(v=vs.100))   
 [Visualización de datos en el depurador](../debugger/viewing-data-in-the-debugger.md)   
 [Especificar archivos de código fuente y símbolos (.pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)