---
title: "VSInstr | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "herramientas de rendimiento, instrumentación"
  - "instrumentación, herramienta VSInstr"
  - "herramientas de generación de perfiles, VSInstr"
  - "herramientas de línea de comandos, instrumentación"
  - "línea de comandos, herramientas"
  - "VSInstr"
  - "VSInstr (herramienta)"
  - "herramientas de rendimiento, herramienta VSInstr"
ms.assetid: 7b1334f7-f9b0-4a82-a145-d0607bfa8467
caps.latest.revision: 44
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 44
---
# VSInstr
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La herramienta VSInstr se utiliza para instrumentar binarios.  Se invoca utilizando la sintaxis siguiente:  
  
```  
VSInstr [/U] filename [/options]  
```  
  
 La tabla siguiente describe las opciones de la herramienta VSInstr:  
  
|Opciones|Descripción|  
|--------------|-----------------|  
|**Help** o **?**|Muestra la Ayuda.|  
|**U**|Escribe la salida de la consola redirigida como Unicode.  Debe ser la primera opción especificada.|  
|`@filename`|Especifica el nombre de un archivo de respuesta que contiene una opción de comando por línea.  No utilice comillas tipográficas.|  
|**OutputPath** `:path`|Especifica un directorio de destino para la imagen instrumentada.  Si no se especifica la ruta de los resultados, se cambia el nombre del archivo binario original agregándole "Orig" al final en el mismo directorio y se instrumenta una copia del archivo binario original.|  
|**Exclude** `:funcspec`|Especifica una especificación de función para excluirla de la instrumentación por sondeos.  Resulta de gran utilidad cuando la inserción de análisis de perfiles en una función provoca un resultado imprevisto o no deseado.<br /><br /> No utilice opciones **Exclude** e **Include** que hagan referencia a funciones del mismo binario.<br /><br /> Puede especificar varias especificaciones de funciones con opciones **Exclude** independientes.<br /><br /> `funcspec` se define como:<br /><br /> \[namespaceseparator1\<\>\] \[classseparator2\<\>\] function<br /><br /> \<separator1\> es `::` para código nativo, y `.` para el código administrado.<br /><br /> \<separator2\> siempre es `::`<br /><br /> **Exclude** se admite con cobertura de código.<br /><br /> Se admite el carácter comodín \*.  Por ejemplo, para excluir todas las funciones en un espacio de nombres use:<br /><br /> MyNamespace::\*<br /><br /> Puede utilizar **VSInstr \/DumpFuncs** para enumerar los nombres completos de funciones en el binario especificado.|  
|**Include** `:funcspec`|Define una especificación de función en un binario para la instrumentación con sondeos.  No se instrumenta ninguna otra función de los binarios.<br /><br /> Puede definir varias especificaciones de funciones con opciones **Include** independientes.<br /><br /> No utilice opciones **Include** e **Exclude** que hagan referencia a funciones del mismo binario.<br /><br /> **Include** no se admite con cobertura de código.<br /><br /> `funcspec` se define como:<br /><br /> \[namespaceseparator1\<\>\] \[classseparator2\<\>\] function<br /><br /> \<separator1\> es `::` para código nativo, y `.` para el código administrado.<br /><br /> \<separator2\> siempre es `::`<br /><br /> Se admite el carácter comodín \*.  Por ejemplo, para incluir todas las funciones en un espacio de nombres use:<br /><br /> MyNamespace::\*<br /><br /> Puede utilizar **VSInstr \/DumpFuncs** para enumerar los nombres completos de funciones en el binario especificado.|  
|**DumpFuncs**|Enumera las funciones dentro de la imagen especificada.  No se realiza ninguna instrumentación.|  
|**ExcludeSmallFuncs**|Excluye de la instrumentación las funciones pequeñas, que son funciones cortas que no realizan ninguna llamada de función.  La opción **ExcludeSmallFuncs** proporciona menos sobrecarga de instrumentación y, en consecuencia, mejora la velocidad de instrumentación.<br /><br /> La exclusión de las funciones pequeñas también reduce el tamaño del archivo .vsp y el tiempo requerido para el análisis.|  
|**Mark:**{**Before** `&#124;`  **After** `&#124;`  **Top** `&#124;` **Bottom**}`,funcname,markid`|Inserta una marca de perfil \(un identificador que se utiliza para delimitar los datos de los informes\) que se puede utilizar para identificar el inicio o el final de un intervalo de datos del archivo de informe .vsp.<br /><br /> **Before**  `` : inmediatamente antes de la entrada de la función de destino.<br /><br /> **After**  `` : inmediatamente después de la salida de la función de destino.<br /><br /> **Top**  `` : inmediatamente después de la entrada de la función de destino.<br /><br /> **Bottom**  `` : inmediatamente antes de cada devolución de la función de destino.<br /><br /> `funcname` \(nombre de la función de destino\).<br /><br /> `Markid` \(entero positivo \(largo\) para su uso como identificador de la marca de perfil\).|  
|**Coverage**|Realiza instrumentación de cobertura.  Solo se puede utilizar con las siguientes opciones: **Verbose**, **OutputPath**, **Exclude** y **Logfile**.|  
|**Verbose**|La opción **Verbose** se utiliza para ver información detallada sobre el proceso de instrumentación.|  
|**NoWarn** `[:[Message Number[;Message Number]]]`|Suprime todas las advertencias específicas.<br /><br /> `Message Number` \(número de la advertencia\).  Si se omite `Message Number`, se suprimen todas las advertencias.<br /><br /> Para obtener más información, vea [Advertencias de VSInstr](../profiling/vsinstr-warnings.md).|  
|**Control** `:{` **Thread** `&#124;`  **Process** `&#124;` **Global** `}`|Especifica el nivel de generación de perfiles de las opciones de control de recolección de datos de VSInstr siguientes:<br /><br /> **Start**<br /><br /> **StartOnly**<br /><br /> **Suspend**<br /><br /> **StopOnly**<br /><br /> **SuspendOnly**<br /><br /> **ResumeOnly**<br /><br /> **Thread**  `` : especifica que las funciones de control de la recolección de datos se realizarán en el nivel de subproceso.  Se inicia o se detiene la generación de perfiles únicamente para el subproceso actual.  El estado de generación de perfiles de los demás subprocesos no se ve afectado.  El valor predeterminado es thread.<br /><br /> **Process**  `` : especifica que las funciones de control de la recolección de datos de generación de perfiles se realizarán en el nivel de proceso.  Se inicia o se detiene la generación de perfiles para todos los subprocesos del proceso actual.  El estado de generación de perfiles de los demás procesos no se ve afectado.<br /><br /> **Global**  `` : especifica que las funciones de control de la recolección de datos se realizarán en el nivel global \(para todos los procesos\).<br /><br /> Se produce un error si no se especifica el nivel de generación de perfiles.|  
|**Start** `:{` **Inside** `&#124;` **Outside** `},funcname`|Limita la recolección de datos a la función de destino y a las funciones secundarias a las que esta función llama.<br /><br /> **Inside**  `` : inserta la función StartProfile inmediatamente después de la entrada a la función de destino.  Inserta la función StopProfile inmediatamente antes de cada devolución de la función de destino.<br /><br /> **Outside**  `` : inserta la función StartProfile inmediatamente antes de cada llamada a la función de destino.  Inserta la función StopProfile inmediatamente después de cada llamada a la función de destino.<br /><br /> `funcname` \(nombre de la función de destino\).|  
|**Suspend** `:{` **Inside** `&#124;` **Outside** `},funcname`|Excluye la recolección de datos para la función de destino y las funciones secundarias invocadas por la función.<br /><br /> **Inside**  `` : inserta la función SuspendProfile inmediatamente después de la entrada a la función de destino.  Inserta la función ResumeProfile inmediatamente antes de cada devolución de la función de destino.<br /><br /> **Outside**  `` : inserta la función SuspendProfile inmediatamente antes de la entrada a la función de destino.  Inserta la función ResumeProfile inmediatamente después de la salida de la función de destino.<br /><br /> `funcname` \(nombre de la función de destino\).<br /><br /> Si la función de destino contiene una función StartProfile, la función SuspendProfile se inserta antes de ella.  Si la función de destino contiene una función StopProfile, la función ResumeProfile se inserta después de ella.|  
|**StartOnly:** `{` **Before** `&#124;`  **After** `&#124;`  **Top** `&#124;` **Bottom** `},funcname`|Comienza la recolección de datos durante una generación de perfiles.  Inserta la función API StartProfile en la ubicación especificada.<br /><br /> **Before**  `` : inmediatamente antes de la entrada de la función de destino.<br /><br /> **After**  `` : inmediatamente después de la salida de la función de destino.<br /><br /> **Top**  `` : inmediatamente después de la entrada de la función de destino.<br /><br /> **Bottom**  `` : inmediatamente antes de cada devolución de la función de destino.<br /><br /> `funcname` \(nombre de la función de destino\).|  
|**StopOnly:**{**Before** `&#124;`  **After** `&#124;`  **Top** `&#124;` **Bottom**}`,funcname`|Detiene la recolección de datos durante una generación de perfiles.  Inserta la función StopProfile en la ubicación especificada.<br /><br /> **Before**  `` : inmediatamente antes de la entrada de la función de destino.<br /><br /> **After**  `` : inmediatamente después de la salida de la función de destino.<br /><br /> **Top**  `` : inmediatamente después de la entrada de la función de destino.<br /><br /> **Bottom**  `` : inmediatamente antes de cada devolución de la función de destino.<br /><br /> `funcname` \(nombre de la función de destino\).|  
|**SuspendOnly:**{**Before** `&#124;`  **After** `&#124;`  **Top** `&#124;` **Bottom**}`,funcname`|Detiene la recolección de datos durante una generación de perfiles.  Inserta la API SuspendProfile en la ubicación especificada.<br /><br /> **Before**  `` : inmediatamente antes de la entrada de la función de destino.<br /><br /> **After**  `` : inmediatamente después de la salida de la función de destino.<br /><br /> **Top**  `` : inmediatamente después de la entrada de la función de destino.<br /><br /> **Bottom**  `` : inmediatamente antes de cada devolución de la función de destino.<br /><br /> `funcname` \(nombre de la función de destino\).<br /><br /> Si la función de destino contiene una función StartProfile, la función SuspendProfile se inserta antes de ella.|  
|**ResumeOnly:**{**Before** `&#124;`  **After** `&#124;`  **Top** `&#124;` **Bottom**}`,funcname`|Comienza o reanuda la recolección de datos durante una generación de perfiles.<br /><br /> Normalmente se utiliza para iniciar la generación de perfiles después de que una opción **SuspendOnly** la haya detenido.  Inserta una API ResumeProfile en la ubicación especificada.<br /><br /> **Before**  `` : inmediatamente antes de la entrada de la función de destino.<br /><br /> **After**  `` : inmediatamente después de la salida de la función de destino.<br /><br /> **Top**  `` : inmediatamente después de la entrada de la función de destino.<br /><br /> **Bottom**  `` : inmediatamente antes de cada devolución de la función de destino.<br /><br /> `funcname` \(nombre de la función de destino\).<br /><br /> Si la función de destino contiene una función StopProfile, la función ResumeProfile se inserta después de ella.|  
  
## Vea también  
 [VSPerfMon](../profiling/vsperfmon.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [VSPerfReport](../profiling/vsperfreport.md)   
 [Advertencias de VSInstr](../profiling/vsinstr-warnings.md)   
 [Vistas de informes de las herramientas de generación de perfiles](../profiling/performance-report-views.md)