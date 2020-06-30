---
title: Procedimiento Crear un informe de seguimiento de llamadas de las Herramientas de generación de perfiles | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, viewing ETW data
- ETW [Visual Studio ALM], viewing data
ms.assetid: 7640520a-7d3c-456c-b184-872a5d2f82f3
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fbf92b38f9408455e10048fbd4a5e84fdf822ea2
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547997"
---
# <a name="how-to-create-a-profiling-tools-call-trace-report"></a>Cómo: Crear un informe de seguimiento de llamadas de las Herramientas de generación de perfiles
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El *informe de seguimiento de llamadas* de las herramientas de generación de perfiles de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] muestra información de intervalos de cada punto de entrada y salida de las funciones de la aplicación y cada llamada a otras funciones realizadas por su función. Los informes de seguimiento de llamadas solo están disponibles para los datos de generación de perfiles si se recopilaron con el método de instrumentación.  
  
> [!NOTE]
> Los informes de seguimiento de llamadas no se pueden mostrar en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Debe utilizar la herramienta de línea de comandos **VSPerfReport** para generar un archivo de valores separados por comas (. csv) o XML. Para obtener más información sobre esta herramienta, vea [VSPerfReport](../profiling/vsperfreport.md).  
  
### <a name="to-create-a-call-trace-report"></a>Para crear un informe de seguimiento de llamadas  
  
1. Abra una ventana del **símbolo del sistema**.  
  
2. En el símbolo del sistema, escriba el siguiente comando:  
  
     *ToolsPath* **VSPerfReport** *VSPFile* **/CallTrace [/Xml]**  
  
    |Command, elemento|Descripción|
    |-|-|  
    |*ToolsPath*|Ruta de acceso a las herramientas de línea de comandos de las herramientas de generación de perfiles. Para obtener más información, consulte [Especificar la ruta de acceso a las herramientas de línea de comandos](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|  
    |*VSPFile*|El archivo de datos de generación de perfiles (.vsp o .vsps). Se aceptan rutas de acceso completas y parciales.|  
    |Xml|Genera un informe con formato XML.|  
  
## <a name="see-also"></a>Consulte también  
 [Cómo: recopilar datos de seguimiento de eventos para Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)   
 [APIs de herramientas de generación de perfiles](../profiling/profiling-tools-apis.md)
