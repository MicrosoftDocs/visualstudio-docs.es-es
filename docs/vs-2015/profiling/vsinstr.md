---
title: VSInstr | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- performance tools, instrumentation
- instrumentation, VSInstr tool
- profiling tools,VSInstr
- command-line tools, instrumentation
- command line, tools
- VSInstr
- VSInstr tool
- performance tools, VSInstr tool
ms.assetid: 7b1334f7-f9b0-4a82-a145-d0607bfa8467
caps.latest.revision: 49
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d905a7a6fa99afa0e7d43409ca1d7b53e7fbd9b0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51773332"
---
# <a name="vsinstr"></a>VSInstr
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La herramienta VSInstr se utiliza para instrumentar binarios. Se invoca mediante la siguiente sintaxis:  
  
```  
VSInstr [/U] filename [/options]  
```  
  
 En la siguiente tabla se describen las opciones de la herramienta VSInstr:  
  
|Opciones|Descripción|  
|-------------|-----------------|  
|**Ayuda** o **?**|Muestra información de ayuda.|  
|**U**|Escribe la salida de la consola redirigida como Unicode. Debe ser la primera opción especificada.|  
|`@filename`|Especifica el nombre de un archivo de respuesta que contiene una opción de comando por línea.  No utilice las comillas.|  
|**OutputPath** `:path`|Especifica un directorio de destino para la imagen instrumentada. Si no se especifica una ruta de acceso de salida, se cambia el nombre del binario original agregándole "Orig" al nombre de archivo en el mismo directorio y se instrumenta una copia del binario.|  
|**Exclude** `:funcspec`|Especifica una especificación de función para excluir de la instrumentación por sondeos. Es útil cuando la inserción de sondeos de generación de perfiles en una función da lugar a resultados impredecibles o no deseados.<br /><br /> No utilice opciones **Exclude** e **Include** que hagan referencia a funciones del mismo binario.<br /><br /> Puede especificar varias especificaciones de funciones con opciones **Exclude** independientes.<br /><br /> `funcspec` se define como:<br /><br /> [namespace\<separator1>] [class\<separator2>]function<br /><br /> \<separator1> es `::` para código nativo, y `.` para código administrado.<br /><br /> \<separator2> siempre es `::`<br /><br /> **Exclude** es compatible con cobertura de código.<br /><br /> Se admite el carácter comodín \*. Por ejemplo, para excluir todas las funciones en un espacio de nombres use:<br /><br /> MyNamespace::\*<br /><br /> Puede usar **VSInstr /DumpFuncs** para enumerar los nombres completos de funciones en el binario especificado.|  
|**Include** `:funcspec`|Especifica una especificación de función en un binario para la instrumentación con sondeos. No se instrumentan el resto de funciones en los binarios.<br /><br /> Puede especificar varias especificaciones de funciones con opciones **Include** independientes.<br /><br /> No utilice opciones **Include** y **Exclude** que hagan referencia a funciones del mismo binario.<br /><br /> **Include** no es compatible con cobertura de código.<br /><br /> `funcspec` se define como:<br /><br /> [namespace\<separator1>] [class\<separator2>]function<br /><br /> \<separator1> es `::` para código nativo, y `.` para código administrado.<br /><br /> \<separator2> siempre es `::`<br /><br /> Se admite el carácter comodín \*. Por ejemplo, para incluir todas las funciones en un espacio de nombres use:<br /><br /> MyNamespace::\*<br /><br /> Puede usar **VSInstr /DumpFuncs** para enumerar los nombres completos de funciones en el binario especificado.|  
|**DumpFuncs**|Enumera las funciones en la imagen especificada. No se realiza ninguna instrumentación.|  
|**ExcludeSmallFuncs**|Excluye de la instrumentación las funciones pequeñas, que son funciones cortas que no realizan ninguna llamada de función. La opción **ExcludeSmallFuncs** proporciona menos sobrecarga de instrumentación y, por tanto, una velocidad de instrumentación mejorada.<br /><br /> La exclusión de las funciones pequeñas también reduce el tamaño del archivo .vsp y el tiempo necesario para el análisis.|  
|**Mark:**{**Before**`&#124;`**After**`&#124;`**Top**`&#124;`**Bottom**}`,funcname,markid`|Inserta una marca de perfil (un identificador utilizado para delimitar los datos de informes) que puede utilizar para identificar el inicio o final de un intervalo de datos en el archivo de informe .vsp.<br /><br /> **Before**: inmediatamente antes de la entrada de la función de destino.<br /><br /> **After**: inmediatamente después de la salida de la función de destino.<br /><br /> **Top**: inmediatamente después de la entrada de la función de destino.<br /><br /> **Bottom**: inmediatamente antes de cada devolución de la función de destino.<br /><br /> `funcname`: nombre de la función de destino<br /><br /> `Markid`: un entero positivo (largo) que se usará como el identificador de la marca de perfil.|  
|**Coverage**|Realiza instrumentación de cobertura. Solo se puede utilizar con las siguientes opciones: **Verbose**, **OutputPath**, **Exclude** y **Logfile**.|  
|**Verbose**|La opción **Verbose** se utiliza para ver información detallada sobre el proceso de instrumentación.|  
|**NoWarn** `[:[Message Number[;Message Number]]]`|Suprime todas las advertencias o solo advertencias específicas.<br /><br /> `Message Number`: el número de advertencia. Si se omite `Message Number`, se suprimen todas las advertencias.<br /><br /> Para obtener más información, consulte [Advertencias de VSInstr](../profiling/vsinstr-warnings.md).|  
|**Control** `:{` **Thread** `&#124;` **Process** `&#124;` **Global** `}`|Especifica el nivel de generación de perfiles de las siguientes opciones de control de recopilación de datos de VSInstr:<br /><br /> **Start**<br /><br /> **StartOnly**<br /><br /> **Suspend**<br /><br /> **StopOnly**<br /><br /> **SuspendOnly**<br /><br /> **ResumeOnly**<br /><br /> **Thread**: especifica las funciones de control de recopilación de datos de nivel de subproceso. La generación de perfiles se inicia o detiene solo para el subproceso actual. El estado de generación de perfiles de otros subprocesos no se ve afectado. El valor predeterminado es thread.<br /><br /> **Process**: especifica las funciones de control de recopilación de datos de generación de perfiles de nivel de proceso. La generación de perfiles se inicia o se detiene en todos los subprocesos del proceso actual. No se ve afectado el estado de generación de perfiles de otros procesos.<br /><br /> **Global**: especifica las funciones de control de recopilación de datos de nivel global (entre procesos).<br /><br /> Se produce un error si no se especifica el nivel de generación de perfiles.|  
|**Start** `:{` **Inside** `&#124;` **Outside** `},funcname`|Limita la recopilación de datos a la función de destino y las funciones secundarias a las que llama.<br /><br /> **Inside**: inserta la función StartProfile inmediatamente después de la entrada a la función de destino. Inserta la función StopProfile inmediatamente antes de cada devolución de la función de destino.<br /><br /> **Outside**: inserta la función StartProfile inmediatamente antes de cada llamada a la función de destino. Inserta la función StopProfile inmediatamente después de cada llamada a la función de destino.<br /><br /> `funcname`: el nombre de la función de destino.|  
|**Suspend** `:{` **Inside** `&#124;` **Outside** `},funcname`|Excluye la recopilación de datos de la función de destino y las funciones secundarias a las que llama.<br /><br /> **Inside**: inserta la función SuspendProfile inmediatamente después de la entrada a la función de destino. Inserta la función ResumeProfile inmediatamente antes de cada devolución de la función de destino.<br /><br /> **Outside**: inserta la función SuspendProfile inmediatamente antes de la entrada a la función de destino. Inserta la función ResumeProfile inmediatamente después de cada salida de la función de destino.<br /><br /> `funcname`: el nombre de la función de destino.<br /><br /> Si la función de destino contiene una función StartProfile, la función SuspendProfile se inserta antes. Si la función de destino contiene una función StopProfile, la función ResumeProfile se inserta después.|  
|**StartOnly:** `{` **Before** `&#124;` **After** `&#124;` **Top** `&#124;` **Bottom** `},funcname`|Comienza la recopilación de datos durante un proceso de generación de perfiles. Inserta la función de API StartProfile en la ubicación especificada.<br /><br /> **Before**: inmediatamente antes de la entrada de la función de destino.<br /><br /> **After**: inmediatamente después de la salida de la función de destino.<br /><br /> **Top**: inmediatamente después de la entrada de la función de destino.<br /><br /> **Bottom**: inmediatamente antes de cada devolución de la función de destino.<br /><br /> `funcname`: el nombre de la función de destino.|  
|**StopOnly:**{**Before**`&#124;`**After**`&#124;`**Top**`&#124;`**Bottom**}`,funcname`|Detiene la recopilación de datos durante un proceso de generación de perfiles. Inserta la función StopProfile en la ubicación especificada.<br /><br /> **Before**: inmediatamente antes de la entrada de la función de destino.<br /><br /> **After**: inmediatamente después de la salida de la función de destino.<br /><br /> **Top**: inmediatamente después de la entrada de la función de destino.<br /><br /> **Bottom**: inmediatamente antes de cada devolución de la función de destino.<br /><br /> `funcname`: el nombre de la función de destino.|  
|**SuspendOnly:**{**Before**`&#124;`**After**`&#124;`**Top**`&#124;`**Bottom**}`,funcname`|Detiene la recopilación de datos durante un proceso de generación de perfiles. Inserta la función de API SuspendProfile en la ubicación especificada.<br /><br /> **Before**: inmediatamente antes de la entrada de la función de destino.<br /><br /> **After**: inmediatamente después de la salida de la función de destino.<br /><br /> **Top**: inmediatamente después de la entrada de la función de destino.<br /><br /> **Bottom**: inmediatamente antes de cada devolución de la función de destino.<br /><br /> `funcname`: el nombre de la función de destino.<br /><br /> Si la función de destino contiene una función StartProfile, la función SuspendProfile se inserta antes.|  
|**ResumeOnly:**{**Before**`&#124;`**After**`&#124;`**Top**`&#124;`**Bottom**}`,funcname`|Comienza o reanuda la recopilación de datos durante un proceso de generación de perfiles.<br /><br /> Normalmente se utiliza para iniciar la generación de perfiles después de que una opción **SuspendOnly** haya dejado de generar perfiles. Inserta una API ResumeProfile en la ubicación especificada.<br /><br /> **Before**: inmediatamente antes de la entrada de la función de destino.<br /><br /> **After**: inmediatamente después de la salida de la función de destino.<br /><br /> **Top**: inmediatamente después de la entrada de la función de destino.<br /><br /> **Bottom**: inmediatamente antes de cada devolución de la función de destino.<br /><br /> `funcname`: el nombre de la función de destino.<br /><br /> Si la función de destino contiene una función StopProfile, la función ResumeProfile se inserta después.|  
  
## <a name="see-also"></a>Vea también  
 [VSPerfMon](../profiling/vsperfmon.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [VSPerfReport](../profiling/vsperfreport.md)   
 [Advertencias de VSInstr](../profiling/vsinstr-warnings.md)   
 [Vistas de informes de rendimiento](../profiling/performance-report-views.md)



