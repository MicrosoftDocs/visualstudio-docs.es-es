---
title: Creación de un informe ETW de herramientas de generación de perfiles | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: bf5547b3-f6c7-4989-9d47-2fe4f1261444
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a49ab3f00eb74edb3be3f733b3c0d70f8613d862
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-create-a-profiling-tools-etw-report"></a>Cómo: Crear un informe ETW de herramientas de generación de perfiles
El informe Seguimiento de eventos para Windows (ETW) muestra los eventos ETW registrados en una sesión de rendimiento de las herramientas de generación de perfiles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Los datos ETW se recopilan en un archivo binario (.etl). Para obtener más información acerca de este informe, consulte [Informe Seguimiento de eventos para Windows (ETW)](../profiling/event-tracing-for-windows-etw-report.md).  
  
> [!NOTE]
>  No se puede mostrar informes ETW en la interfaz para [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   Para obtener información sobre cómo recopilar datos ETW utilizando la interfaz para [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], vea [Cómo: Recopilar datos de Seguimiento de eventos para Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md).  
  
-   Para obtener información sobre cómo recopilar datos ETW desde un símbolo del sistema, vea [VSPerfCmd](../profiling/vsperfcmd.md) y [Eventos](../profiling/events-vsperfcmd.md).  
  
 Genere el informe ETW utilizando el comando **VSReport/summary:etw**. El .etl que contiene los datos ETW debe estar en el mismo directorio que el archivo de datos de generación de perfiles (.vsp o .vsps). De forma predeterminada, el informe se genera como un archivo de valores separados por comas (.csv). Para obtener más información, consulte [VSPerfReport](../profiling/vsperfreport.md).  
  
### <a name="to-generate-an-etw-report"></a>Para generar un informe ETW  
  
-   En una ventana **Símbolo del sistema**, escriba la línea de comandos siguiente:  
  
     *ToolsPath* **VSPerfReport** *VSPFile*  **/Summary:ETW [/Xml]**  
  
    |||  
    |-|-|  
    |*ToolsPath*|La ruta de acceso de las herramientas de generación de perfiles. Para obtener más información, consulte [Especificar la ruta de acceso a las herramientas de línea de comandos](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|  
    |*VSPFile*|El archivo de datos de generación de perfiles (.vsp o .vsps). Se aceptan rutas de acceso completas y parciales.|  
    |Xml|Genera un informe con formato XML.|