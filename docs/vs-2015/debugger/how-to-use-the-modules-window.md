---
title: 'Cómo: usar la ventana módulos | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.modules
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Modules window
- Modules window
- executable files, displaying while debugging
- debugging [Visual Studio], displaying modules
- DLLs, displaying while debugging
- modules, displaying
ms.assetid: d840fdca-b035-4452-b652-72580c831896
caps.latest.revision: 41
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b592515692e23dce49c125c7895bd158904b653f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696129"
---
# <a name="how-to-use-the-modules-window"></a>Cómo: Utilizar la ventana Módulos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

NOTA]
> Esta característica no está disponible para la depuración de SQL o de script.  
  
 La ventana **módulos** muestra los archivos dll y exe utilizados por el programa y muestra información relevante para cada uno.  
  
### <a name="to-display-the-modules-window-in-break-mode-or-in-run-mode"></a>Para mostrar la ventana Módulos en modo de interrupción o modo de ejecución  
  
- En el menú **depurar** , elija **ventanas**y, a continuación, haga clic en **módulos**.  
  
     De forma predeterminada, la ventana **Módulos** ordena los módulos por orden de carga. No obstante, puede ordenarlos por columnas.  
  
### <a name="to-sort-by-any-column"></a>Para ordenarlos por columnas  
  
- Haga clic en el botón situado en la parte superior de la columna.  
  
     Puede cargar símbolos o especificar una ruta de acceso de símbolos desde la ventana **módulos** mediante el menú contextual.  
  
## <a name="loading-symbols"></a>Cargar Símbolos  
 En la ventana **módulos** , puede ver qué módulos tienen cargados los símbolos de depuración. Esta información aparece en la columna Estado de los **símbolos** . Si el estado indica **omitido loadingCannot buscar o abrir el archivo PDB**, o **cargar deshabilitado por la configuración de inclusión/exclusión**, puede dirigir el depurador para que descargue los símbolos de los servidores de símbolos públicos de Microsoft o para cargar los símbolos desde un directorio de símbolos del equipo. Para obtener más información, vea [especificar archivos de código fuente y símbolos (. pdb).](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)  
  
#### <a name="to-load-symbols-manually"></a>Para cargar símbolos manualmente  
  
1. En la ventana **módulos** , haga clic con el botón secundario en un módulo para el que no se han cargado los símbolos.  
  
2. Seleccione **cargar símbolos desde** y, a continuación, haga clic en **servidores de símbolos de Microsoft** o ruta de acceso de **símbolos**.  
  
#### <a name="to-change-symbol-load-settings"></a>Para cambiar la configuración de carga de símbolos  
  
1. En la ventana **Módulos**, haga clic con el botón derecho en cualquier módulo.  
  
2. Haga clic en **configuración de símbolos**.  
  
     Ahora puede cambiar la configuración de carga de símbolos, tal como se describe en [especificar las ubicaciones de símbolos y el comportamiento de carga](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Specify_symbol_locations_and_loading_behavior). Los cambios no surten efecto hasta que se reinicie la sesión de depuración.  
  
#### <a name="to-change-symbol-load-behavior-for-a-specific-module"></a>Para cambiar el comportamiento de carga de símbolos para un módulo específico  
  
1. En la ventana **Módulos**, haga clic con el botón derecho en el módulo.  
  
2. Seleccione **configuración de carga automática de símbolos** y, a continuación, haga clic en **cargar siempre de forma manual** o **predeterminada**. Los cambios no surten efecto hasta que se reinicie la sesión de depuración.  
  
## <a name="see-also"></a>Consulte también  
 [Interrumpir la ejecución](https://msdn.microsoft.com/30fc4643-f337-4651-b1ff-f2de2c098d40)   
 [Ver datos en el depurador](../debugger/viewing-data-in-the-debugger.md)   
 [Especificar archivos de código fuente y símbolos (.pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
