---
title: Procedimiento Usar el registro de actividad | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, debugging
- VSPackages, troubleshooting
ms.assetid: bb3d3322-0e5e-4dd5-b93a-24d5fbcd2ffd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9305cf1de6cadc2230b90723ac0f995b425ba3a5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53990339"
---
# <a name="how-to-use-the-activity-log"></a>Procedimiento Usar el registro de actividad
Los VSPackages pueden escribir mensajes en el registro de actividad. Esta característica es especialmente útil para depurar los VSPackages en establecimientos comerciales.  
  
> [!TIP]
>  El registro de actividad está siempre activado. Visual Studio mantiene un búfer gradual de las últimas 100 entradas, así como las 10 primeras entradas, que tienen información de configuración general.  
  
## <a name="to-write-an-entry-to-the-activity-log"></a>Para escribir una entrada en el registro de actividad  
  
1.  Inserte este código en el <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> método o en cualquier otro método excepto en el constructor de VSPackage:  
  
    ```csharp  
    IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (log == null) return;  
  
    int hr = log.LogEntry((UInt32)__ACTIVITYLOG_ENTRYTYPE.ALE_INFORMATION,  
        this.ToString(),  
        string.Format(CultureInfo.CurrentCulture,  
        "Called for: {0}", this.ToString()));  
    ```  
  
     Este código obtiene el <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> de servicio y lo convierte a un <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interfaz. <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A> escribe una entrada informativa en el registro de actividad utilizando el contexto de la referencia cultural actual.  
  
2.  Cuando se carga el VSPackage (normalmente, cuando se invoca un comando o se abre una ventana), el texto se escribe en el registro de actividad.  
  
## <a name="to-examine-the-activity-log"></a>Para examinar el registro de actividad  
  
1. Ejecutar Visual Studio con el [/Log](../ide/reference/log-devenv-exe.md) modificador de línea de comandos para escribir ActivityLog.xml en el disco durante la sesión.

2. Después de cerrar Visual Studio, busque el registro de actividad en la subcarpeta para los datos de Visual Studio:  <em>*% AppData %</em>\Microsoft\VisualStudio\15.0\ActivityLog.xml*.  
  
3. Abra el registro de actividad con cualquier editor de texto. Aquí es una entrada típica:  
  
   ```  
   Called for: Company.MyApp.MyAppPackage ...  
   ```  
  
## <a name="robust-programming"></a>Programación sólida  
 Dado que el registro de actividad es un servicio, el registro de actividad no está disponible en el constructor de VSPackage.  
  
 Debe obtener el registro de actividad justo antes de escribir en él. No se almacene en caché o guardar el registro de actividad para un uso futuro.  
  
## <a name="see-also"></a>Vea también
 [/Log (devenv.exe)](../ide/reference/log-devenv-exe.md)   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE>   
 [Solucionar problemas de VSPackages](../extensibility/troubleshooting-vspackages.md)   
 [VSPackages](../extensibility/internals/vspackages.md)
