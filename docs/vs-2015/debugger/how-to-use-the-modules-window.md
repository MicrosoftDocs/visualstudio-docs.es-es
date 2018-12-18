---
title: 'Cómo: utilizar la ventana módulos | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: fea513b7593e260b5f5fb71e40ced98a1f8cc279
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51764408"
---
# <a name="how-to-use-the-modules-window"></a>Cómo: Utilizar la ventana Módulos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

NOTA]
>  Esta característica no está disponible para la depuración de SQL o de script.  
  
 El **módulos** ventana enumera los archivos DLL y EXE que son utilizados por el programa y muestra información pertinente para cada uno.  
  
### <a name="to-display-the-modules-window-in-break-mode-or-in-run-mode"></a>Para mostrar la ventana Módulos en modo de interrupción o modo de ejecución  
  
-   En el **depurar** menú, elija **Windows**y, a continuación, haga clic en **módulos**.  
  
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
 [Interrumpir la ejecución](http://msdn.microsoft.com/en-us/30fc4643-f337-4651-b1ff-f2de2c098d40)   
 [Visualización de datos en el depurador](../debugger/viewing-data-in-the-debugger.md)   
 [Especificar archivos de código fuente y símbolos (.pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)





