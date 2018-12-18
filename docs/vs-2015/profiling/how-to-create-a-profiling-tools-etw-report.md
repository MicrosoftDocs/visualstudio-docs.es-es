---
title: Creación de un informe ETW de herramientas de generación de perfiles | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bf5547b3-f6c7-4989-9d47-2fe4f1261444
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1901cf0800483ee4ce8ba0bce26fe3cf7ac073e6
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51761599"
---
# <a name="how-to-create-a-profiling-tools-etw-report"></a>Cómo: Crear un informe ETW de herramientas de generación de perfiles
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El informe Seguimiento de eventos para Windows (ETW) muestra los eventos ETW registrados en una sesión de rendimiento de las herramientas de generación de perfiles de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Los datos ETW se recopilan en un archivo binario (.etl). Para obtener más información acerca de este informe, consulte [Informe Seguimiento de eventos para Windows (ETW)](../profiling/event-tracing-for-windows-etw-report.md).  
  
> [!NOTE]
>  No se puede mostrar informes ETW en la interfaz para [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
- Para obtener información sobre cómo recopilar datos ETW utilizando la interfaz para [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], vea [Cómo: Recopilar datos de Seguimiento de eventos para Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md).  
  
- Para obtener información sobre cómo recopilar datos ETW desde un símbolo del sistema, vea [VSPerfCmd](../profiling/vsperfcmd.md) y [Eventos](../profiling/events-vsperfcmd.md).  
  
  Genere el informe ETW utilizando el comando **VSReport/summary:etw**. El .etl que contiene los datos ETW debe estar en el mismo directorio que el archivo de datos de generación de perfiles (.vsp o .vsps). De forma predeterminada, el informe se genera como un archivo de valores separados por comas (.csv). Para obtener más información, consulte [VSPerfReport](../profiling/vsperfreport.md).  
  
### <a name="to-generate-an-etw-report"></a>Para generar un informe ETW  
  
-   En una ventana **Símbolo del sistema**, escriba la línea de comandos siguiente:  
  
     *ToolsPath* **VSPerfReport** *VSPFile*  **/Summary:ETW [/Xml]**  
  
    |||  
    |-|-|  
    |*ToolsPath*|La ruta de acceso de las herramientas de generación de perfiles. Para obtener más información, consulte [Especificar la ruta de acceso a las herramientas de línea de comandos](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|  
    |*VSPFile*|El archivo de datos de generación de perfiles (.vsp o .vsps). Se aceptan rutas de acceso completas y parciales.|  
    |Xml|Genera un informe con formato XML.|



