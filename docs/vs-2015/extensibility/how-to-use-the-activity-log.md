---
title: Procedimiento Usar el registro de actividad | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, debugging
- VSPackages, troubleshooting
ms.assetid: bb3d3322-0e5e-4dd5-b93a-24d5fbcd2ffd
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 812862c3eaf99b7459bb422e174f8fe155ea384a
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60042592"
---
# <a name="how-to-use-the-activity-log"></a>Procedimiento Uso del registro de actividad
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los VSPackages pueden escribir mensajes en el registro de actividad. Esta característica es especialmente útil para depurar los VSPackages en establecimientos comerciales.  
  
> [!TIP]
>  El registro de actividad está siempre activado. Visual Studio mantiene un búfer gradual de las entradas de cien por última vez, así como las diez primeras entradas, que tienen información de configuración general.  
  
### <a name="to-write-an-entry-to-the-activity-log"></a>Para escribir una entrada en el registro de actividad  
  
1. Inserte este código en el <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> método o en cualquier otro método excepto en el constructor de VSPackage:  
  
    ```csharp  
    IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (log == null) return;  
  
    int hr = log.LogEntry((UInt32)__ACTIVITYLOG_ENTRYTYPE.ALE_INFORMATION,  
        this.ToString(),  
        string.Format(CultureInfo.CurrentCulture,  
        "Called for: {0}", this.ToString()));  
    ```  
  
     Este código obtiene el <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> de servicio y lo convierte a un <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interfaz. <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A> escribe una entrada informativa en el registro de actividad utilizando el contexto de la referencia cultural actual.  
  
2. Cuando se carga el VSPackage (normalmente, cuando se invoca un comando o se abre una ventana), el texto se escribe en el registro de actividad.  
  
### <a name="to-examine-the-activity-log"></a>Para examinar el registro de actividad  
  
1. Encontrar el registro de actividad en la subcarpeta de datos de Visual Studio: *% AppData %* \Microsoft\VisualStudio\14.0\ActivityLog.XML...  
  
2. Abra el registro de actividad con cualquier editor de texto. Aquí es una entrada típica:  
  
    ```  
    Called for: Company.MyApp.MyAppPackage ...  
    ```  
  
## <a name="robust-programming"></a>Programación sólida  
 Dado que el registro de actividad es un servicio, el registro de actividad no está disponible en el constructor de VSPackage.  
  
 Debe obtener el registro de actividad justo antes de escribir en él. No se almacene en caché o guardar el registro de actividad para un uso futuro.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE>   
 [Solucionar problemas de VSPackages](../extensibility/troubleshooting-vspackages.md)   
 [VSPackages](../extensibility/internals/vspackages.md)
