---
title: Procedimiento Crear un informe de seguimiento de llamadas de las Herramientas de generación de perfiles | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, viewing ETW data
- ETW [Visual Studio ALM], viewing data
ms.assetid: 7640520a-7d3c-456c-b184-872a5d2f82f3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c2d48b266108a053fa24da517d2367fe85b2b6a6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53985870"
---
# <a name="how-to-create-a-profiling-tools-call-trace-report"></a>Procedimiento Crear un informe de seguimiento de llamadas de las herramientas de generación de perfiles
El *informe de seguimiento de llamadas* de las herramientas de generación de perfiles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] muestra información de intervalos de cada punto de entrada y salida de las funciones de la aplicación y cada llamada a otras funciones realizadas por su función. Los informes de seguimiento de llamadas solo están disponibles para los datos de generación de perfiles si se recopilaron con el método de instrumentación.  
  
> [!NOTE]
>  Los informes de seguimiento de llamadas no se pueden mostrar en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Debe usar la herramienta de línea de comandos **VSPerfReport** para generar un archivo de valores separados por comas (.*csv*) o .*xml*. Para obtener más información sobre esta herramienta, vea [VSPerfReport](../profiling/vsperfreport.md).  
  
### <a name="to-create-a-call-trace-report"></a>Para crear un informe de seguimiento de llamadas  
  
1.  Abra una ventana de **Símbolo del sistema**.  
  
2.  En el símbolo del sistema, escriba el siguiente comando:  
  
     *ToolsPath* **VSPerfReport** *VSPFile* **/CallTrace [/Xml]**  
  
    |||  
    |-|-|  
    |*ToolsPath*|Ruta de acceso a las herramientas de línea de comandos de las Herramientas de generación de perfiles. Para más información, vea [Especificar la ruta de acceso a las herramientas de línea de comandos](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|  
    |*VSPFile*|El archivo de datos de generación de perfiles (.*vsp* o .*vsps*). Se aceptan rutas de acceso completas y parciales.|  
    |Xml|Genera un informe con formato XML.|  

  
## <a name="see-also"></a>Vea también  
 [Cómo: Recopilar datos de seguimiento de eventos para Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)   
 [API de herramientas de generación de perfiles](../profiling/profiling-tools-apis.md)
