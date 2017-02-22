---
title: "C&#243;mo: utilizar el registro de actividad | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSPackages, depuración"
  - "VSPackages, solución de problemas"
ms.assetid: bb3d3322-0e5e-4dd5-b93a-24d5fbcd2ffd
caps.latest.revision: 29
caps.handback.revision: 29
ms.author: "gregvanl"
manager: "ghogen"
---
# C&#243;mo: utilizar el registro de actividad
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VSPackages puede escribir mensajes en el registro de actividad. Esta característica es especialmente útil para depurar los VSPackages en establecimientos comerciales.  
  
> [!TIP]
>  Siempre está activado el registro de actividad. Visual Studio mantiene un búfer gradual de las entradas de la última cien, así como las diez primeras entradas, que tienen información de configuración general.  
  
### Para escribir una entrada en el registro de actividad  
  
1.  Inserte este código en el <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> método o en cualquier otro método excepto el constructor de VSPackage:  
  
    ```c#  
    IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (log == null) return;  
  
    int hr = log.LogEntry((UInt32)__ACTIVITYLOG_ENTRYTYPE.ALE_INFORMATION,  
        this.ToString(),  
        string.Format(CultureInfo.CurrentCulture,  
        "Called for: {0}", this.ToString()));  
    ```  
  
     Este código obtiene el <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> de servicio y lo convierte a un <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interfaz.<xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A> escribe una entrada informativa en el registro de actividad mediante el contexto de la referencia cultural actual.  
  
2.  Cuando se carga el paquete VSPackage \(normalmente, cuando se invoca un comando o se abre una ventana\), el texto se escribe en el registro de actividad.  
  
### Para examinar el registro de actividad  
  
1.  Buscar el registro de actividad en la subcarpeta para los datos de Visual Studio: *% AppData %*\\Microsoft\\VisualStudio\\14.0\\ActivityLog.XML...  
  
2.  Abra el registro de actividad con cualquier editor de texto. Aquí es una entrada típica:  
  
    ```  
    Called for: Company.MyApp.MyAppPackage ...  
    ```  
  
## Programación eficaz  
 Dado que el registro de actividad es un servicio, el registro de actividad no está disponible en el constructor de VSPackage.  
  
 Debe obtener el registro de actividad justo antes de escribir en él. No almacenar en memoria caché o guardar el registro de actividad para un uso futuro.  
  
## Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE>   
 [Solucionar problemas de VSPackages](../extensibility/troubleshooting-vspackages.md)   
 [VSPackages](../extensibility/internals/vspackages.md)