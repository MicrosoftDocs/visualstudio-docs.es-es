---
title: VSPerfMon | Microsoft Docs
description: Obtenga más información sobre cómo puede usar la herramienta VSPerfMon para recopilar datos de rendimiento de una aplicación. Esta herramienta normalmente se suele iniciar mediante VSPerfCmd.exe.
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSPerfMon tool
- command line, tools
- command-line tools, VSPerfMon tool
- data [Visual Studio ALM], VSPerfMon tool
- performance data, VSPerfMon tool
- performance tools, VSPerfMon tool
- profilng tools,VSPerfCmd
ms.assetid: 37052afb-7a58-441f-bb17-f1587cc57068
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 919153699299c2f39ad0353ed484a9f9c9f46846
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2021
ms.locfileid: "98719180"
---
# <a name="vsperfmon"></a>VSPerfMon
La herramienta VSPerfMon, que normalmente suele iniciar *VSPerfCmd.exe*, se puede usar para recopilar los datos de rendimiento de una aplicación. VSPerfMon muestra información adicional sobre el proceso de adjuntar o separar que no está disponible mediante la herramienta VSPerfCmd. Para ver esta información, inicie VSPerfMon en una ventana independiente. Para invocar VSPerfMon, utilice la siguiente sintaxis:

```cmd
VSPerfMon [/U] </TRACE [/COUNTER:cfg] | /SAMPLE | /COVERAGE> /CROSSSESSION /OUTPUT <file name> [/WINCOUNTER:cfg] [/USER [DOMAIN\]username]
```

 En la siguiente tabla se describen las opciones de la herramienta VSPerfMon:

|Opciones|Descripción|
|-------------|-----------------|
|**U**|Se escribe la salida de la consola redirigida como Unicode.  Esta debe ser la primera opción especificada.|
|**OUTPUT:** `<` *file name* `>`|Redirige la salida al nombre de archivo especificado.|
|**TRACE**|Inicia el monitor de rendimiento para la generación de perfiles instrumentada.|
|**SAMPLE**|Inicia el monitor de rendimiento para la generación de perfiles de muestreo.|
|**COVERAGE**|Inicia el monitor de rendimiento para la recolección de cobertura de código.|
|**CONCURRENCY**|Inicia al monitor de rendimiento para la generación de perfiles de contención de recursos.|
|**USER:** `[` *domain* `\]` *username*|Permite el acceso de cliente al monitor de rendimiento desde la cuenta especificada.|
|**CROSSSESSION**|Permite la generación de perfiles entre sesiones.|
|**COUNTER** `:cfg`|Cuando se utiliza el método de generación de perfiles instrumentación (TRACE), especifica un contador de CPU que se recopila en cada punto de instrumentación. Puede recopilar datos de varios contadores especificando varias opciones Counter.<br /><br /> Utilice la siguiente sintaxis para especificar los datos del contador (*cfg*):<br /><br /> **CounterName** [**,Reload**[,**FriendlyName**]]<br /><br /> -   **CounterName** es el nombre de un contador devuelto por el comando /QueryCounters de VSPerfCmd.<br />-   **Reload** es el intervalo de muestreo de eventos de contador. No utilice *Reload* con el método de instrumentación.<br />-   Cuando se especifica, **FriendlyName** reemplaza **CounterName** en los nombres de columna del informe de herramientas de generación de perfiles.|
|**WINCOUNTER** `:path`|Especifica un contador de rendimiento de Windows que se incluirá con datos de marca. `path` es una cadena de contador de rendimiento de Windows en formato de ruta de acceso de contador PDH. Por ejemplo:<br /><br /> \Processor(0)\\% Processor Time<br /><br /> \System\Context Switches/sec|
|**AUTOMARK** `:n`|Especifica el intervalo de tiempo (en milisegundos) entre marcas automáticas cuando se usa /WINCOUNTER. Redondeado a los 500 ms más cercanos.<br /><br /> Use 0 para deshabilitar las marcas automáticas. (predeterminado = 500 ms si no se especifica)|

## <a name="see-also"></a>Vea también
- [VSInstr](../profiling/vsinstr.md)
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [VSPerfReport](../profiling/vsperfreport.md)
- [Vistas de informes de rendimiento](../profiling/performance-report-views.md)
