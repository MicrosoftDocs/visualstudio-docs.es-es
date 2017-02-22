---
title: "VSPerfMon | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSPerfMon (herramienta)"
  - "línea de comandos, herramientas"
  - "herramientas de línea de comandos, herramienta VSPerfMon"
  - "datos [Visual Studio ALM], herramienta VSPerfMon"
  - "datos de rendimiento, herramienta VSPerfMon"
  - "herramientas de rendimiento, herramienta VSPerfMon"
  - "herramientas de generación de perfiles, VSPerfCmd"
ms.assetid: 37052afb-7a58-441f-bb17-f1587cc57068
caps.latest.revision: 30
caps.handback.revision: 30
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# VSPerfMon
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede utilizar la herramienta VSPerfMon para recopilar datos de rendimiento de una aplicación; esta herramienta la suele iniciar VSPerfCmd.exe.  VSPerfMon muestra información adicional sobre la asociación y desasociación de procesos, que no está disponible con la herramienta VSPerfCmd.  Para ver esta información, inicie VSPerfMon en una ventana independiente.  Para invocar VSPerfMon, utilice la sintaxis siguiente:  
  
```  
VSPerfMon [/U] </TRACE [/COUNTER:cfg] | /SAMPLE | /COVERAGE> /CROSSSESSION /OUTPUT <file name> [/WINCOUNTER:cfg] [/USER [DOMAIN\]username]  
```  
  
 La tabla siguiente describe las opciones de la herramienta VSPerfMon:  
  
|Opciones|Descripción|  
|--------------|-----------------|  
|**U**|La salida de la consola redirigida se escribe como Unicode.  Debe ser la primera opción especificada.|  
|**OUTPUT:** `<` *file name* `>`|Redirige el resultado al nombre de archivo especificado.|  
|**TRACE**|Inicia el monitor de rendimiento para la generación de perfiles instrumentada.|  
|**SAMPLE**|Inicia el monitor de rendimiento para la generación de perfiles de muestreo.|  
|**COVERAGE**|Inicia el monitor de rendimiento para la recolección de cobertura de código.|  
|**CONCURRENCY**|Inicia el monitor de rendimiento para generar perfiles de contención de recursos.|  
|**USER:** `[` *domain* `\]` *username*|Permite el acceso de cliente al monitor de rendimiento desde la cuenta especificada.|  
|**CROSSSESSION**|Habilita la generación de perfiles entre sesiones.|  
|**COUNTER** `:cfg`|Cuando se utiliza el método de generación de perfiles de instrumentación \(TRACE\), especifica un contador de CPU que se va a recopilar en cada punto de instrumentación.  Para recopilar múltiples datos de contador, especifique varias opciones Counter.<br /><br /> Utilice la siguiente sintaxis para especificar los datos del contador \(de*cfg*\):<br /><br /> CounterName\[**,**Reload\[,FriendlyName\]\]<br /><br /> -   CounterName es el nombre de un contador devuelto por el comando \/QueryCounters de VSPerfCmd.<br />-   Reload es el intervalo de muestreo del evento de contador.  No utilice *Reload* con el método de instrumentación.<br />-   Cuando se especifica, FriendlyName reemplaza a CounterName en los nombres de columnas de informes de las herramientas de generación de perfiles.|  
|**WINCOUNTER** `:path`|Especifica un contador de rendimiento de Windows para incluirlo con datos de marcas.  `path` es una cadena del contador de rendimiento de Windows en el formato de ruta de acceso de contador PDH.  Por ejemplo:<br /><br /> \\Processor\(0\)\\% Processor Time<br /><br /> \\System\\Context Switches\/sec|  
|**AUTOMARK** `:n`|Especifica el intervalo \(en milisegundos\) entre marcas automáticas cuando se usa \/WINCOUNTER.  Redondea al alza a los 500 ms más próximos.<br /><br /> Use 0 para deshabilitar las marcas automáticas. \(valor predeterminado \= 500 ms si no se especifica\)|  
  
## Vea también  
 [VSInstr](../profiling/vsinstr.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [VSPerfReport](../profiling/vsperfreport.md)   
 [Vistas de informes de las herramientas de generación de perfiles](../profiling/performance-report-views.md)