---
title: Procedimiento Crear un informe ETW de Herramientas de generación de perfiles | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: bf5547b3-f6c7-4989-9d47-2fe4f1261444
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 20b7c92c8cbbf500b44816fbb0f34e0df6f04720
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54940939"
---
# <a name="how-to-create-a-profiling-tools-etw-report"></a>Procedimiento Crear un informe ETW de herramientas de generación de perfiles
El informe Seguimiento de eventos para Windows (ETW) muestra los eventos ETW registrados en una sesión de rendimiento de las herramientas de generación de perfiles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Los datos ETW se recopilan en un archivo binario (.*etl*). Para obtener más información sobre este informe, vea [Informe Seguimiento de eventos para Windows (ETW)](../profiling/event-tracing-for-windows-etw-report.md).  
  
> [!NOTE]
>  No se puede mostrar informes ETW en la interfaz para [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
- Para obtener información sobre cómo recopilar datos ETW mediante la interfaz de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], vea [Cómo: Recopilar datos de seguimiento de eventos para Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md).  
  
- Para obtener información sobre cómo recopilar datos ETW desde un símbolo del sistema, vea [VSPerfCmd](../profiling/vsperfcmd.md) y [Eventos](../profiling/events-vsperfcmd.md).  
  
  Genere el informe ETW utilizando el comando **VSReport/summary:etw**. El .*etl* que contiene los datos ETW debe estar en el mismo directorio que el archivo de datos de generación de perfiles (.*vsp* o .*vsps*). De forma predeterminada, el informe se genera como un archivo de valores separados por comas (.*csv*). Para obtener más información, consulte [VSPerfReport](../profiling/vsperfreport.md).  
  
### <a name="to-generate-an-etw-report"></a>Para generar un informe ETW  
  
-   En una ventana **Símbolo del sistema**, escriba la línea de comandos siguiente:  
  
     *ToolsPath* **VSPerfReport** *VSPFile*  **/Summary:ETW [/Xml]**  
  
    |||  
    |-|-|  
    |*ToolsPath*|La ruta de acceso de las herramientas de generación de perfiles. Para más información, vea [Especificar la ruta de acceso a las herramientas de línea de comandos](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|  
    |*VSPFile*|El archivo de datos de generación de perfiles (.*vsp* o .*vsps*). Se aceptan rutas de acceso completas y parciales.|  
    |Xml|Genera un informe con formato XML.|
