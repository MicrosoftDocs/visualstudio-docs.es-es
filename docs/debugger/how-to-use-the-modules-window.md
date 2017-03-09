---
title: "C&#243;mo: Utilizar la ventana M&#243;dulos | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.modules"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "depurador, ventana Módulos"
  - "Módulos (ventana)"
  - "archivos ejecutables, mostrar al depurar"
  - "depurar [Visual Studio], mostrar módulos"
  - "DLL, mostrar al depurar"
  - "módulos, mostrar"
ms.assetid: d840fdca-b035-4452-b652-72580c831896
caps.latest.revision: 36
caps.handback.revision: 36
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# C&#243;mo: Utilizar la ventana M&#243;dulos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

> [!NOTE]
>  Esta característica no está disponible para la depuración de SQL o de script.  
  
 En la ventana **Módulos** se indican los archivos DLL y EXE utilizados por el programa y se muestra información relevante acerca de cada uno de ellos.  
  
### Para mostrar la ventana Módulos en modo de interrupción o modo de ejecución  
  
-   En el menú **Depurar**, elija **Ventanas** y haga clic en **Módulos**.  
  
     De forma predeterminada, la ventana **Módulos** ordena los módulos por orden de carga.  No obstante, puede ordenarlos por columnas.  
  
### Para ordenarlos por columnas  
  
-   Haga clic en el botón situado en la parte superior de la columna.  
  
     Puede cargar los símbolos o especificar una ruta de acceso a símbolos desde la ventana **Módulos** mediante el menú contextual.  
  
## Cargar Símbolos  
 En la ventana **Módulos**, puede ver qué módulos han cargado los símbolos de depuración.  Esta información aparece en la columna **Estado del símbolo**.  Si el estado dice **Carga omitida**, **No se puede encontrar o abrir el archivo PDB** o **Carga deshabilitada por la configuración de inclusión o exclusión** puede dirigir el depurador para descargar los símbolos de los servidores de símbolos públicos de Microsoft o cargar los símbolos de una ruta de acceso de un directorio de símbolos del equipo.  Para obtener más información, vea [Especificar archivos de código fuente y símbolos \(.pdb\)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)  
  
#### Para cargar símbolos manualmente  
  
1.  En la ventana **Módulos**, haga clic con el botón secundario en un módulo para el que no se han cargado los símbolos.  
  
2.  Elija **Cargar símbolos desde** y, a continuación, haga clic en **Servidores de símbolos de Microsoft** o **Ruta de acceso de símbolos**.  
  
#### Para cambiar la configuración de carga de símbolos  
  
1.  En la ventana **Módulos**, haga clic con el botón secundario en cualquier módulo.  
  
2.  Haga clic en **Valores de los símbolos**.  
  
     A continuación, puede cambiar la configuración de carga de símbolos como se describe en [Especificar las ubicaciones de símbolos y el comportamiento de carga](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Specify_symbol_locations_and_loading_behavior).  Los cambios no surten efecto hasta que se reinicie la sesión de depuración.  
  
#### Para cambiar el comportamiento de carga de símbolos para un módulo específico  
  
1.  En la ventana **Módulos**, haga clic con el botón secundario en el módulo.  
  
2.  Seleccione **Configuración de carga de símbolos automática** y, a continuación, haga clic en **Cargar siempre manualmente** o en **Predeterminado**.  Los cambios no surten efecto hasta que se reinicie la sesión de depuración.  
  
## Vea también  
 [Breaking Execution](http://msdn.microsoft.com/es-es/30fc4643-f337-4651-b1ff-f2de2c098d40)   
 [Ver datos en el depurador](../debugger/viewing-data-in-the-debugger.md)   
 [Especificar archivos de código fuente y símbolos \(.pdb\)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)