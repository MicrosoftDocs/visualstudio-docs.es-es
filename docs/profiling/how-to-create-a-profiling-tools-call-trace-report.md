---
title: "C&#243;mo: Crear un informe de seguimiento de llamadas de las Herramientas de generaci&#243;n de perfiles | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ETW [Visual Studio ALM], ver datos"
  - "herramientas de rendimiento, ver datos ETW"
ms.assetid: 7640520a-7d3c-456c-b184-872a5d2f82f3
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# C&#243;mo: Crear un informe de seguimiento de llamadas de las Herramientas de generaci&#243;n de perfiles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El *informe de seguimiento de llamadas* de las herramientas de generación de perfiles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] muestra información de tiempos de cada punto de entrada y salida de las funciones de la aplicación y de cada llamada a otras funciones por parte de su función.  Los informes de seguimiento de llamadas solo están disponibles para la generación de perfiles si se recopilaron con el método de instrumentación.  
  
> [!NOTE]
>  No puede mostrar los informes de seguimiento de llamadas en la interfaz de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Debe utilizar la herramienta de línea de comandos **VSPerfReport** para generar un archivo .csv \(valores separados por comas\) o un archivo xml.  Para obtener más información sobre esta herramienta, vea [VSPerfReport](../profiling/vsperfreport.md).  
  
### Para crear un informe de seguimiento de llamadas  
  
1.  Abra una ventana del **símbolo del sistema**.  
  
2.  En el símbolo del sistema, escriba el siguiente comando:  
  
     *ToolsPath* **VSPerfReport** *VSPFile* **\/CallTrace \[\/Xml\]**  
  
    |||  
    |-|-|  
    |*ToolsPath*|La ruta de acceso de las herramientas de línea de comandos de las herramientas de generación de perfiles.  Para obtener más información, vea [Especificar la ruta de acceso a las herramientas de línea de comandos](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|  
    |*VSPFile*|El archivo de datos de generación de perfiles \(.vsp o .vsps\).  Se aceptan rutas de acceso completas y parciales.|  
    |Xml|Genera un informe con formato XML.|  
  
## Vea también  
 [Cómo: Recopilar datos de Seguimiento de eventos para Windows \(ETW\)](../Topic/How%20to:%20Collect%20Event%20Tracing%20for%20Windows%20\(ETW\)%20Data.md)   
 [APIs de herramientas de generación de perfiles](../profiling/profiling-tools-apis.md)