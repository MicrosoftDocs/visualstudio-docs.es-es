---
title: "Cómo: usar el registro de actividad | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, debugging
- VSPackages, troubleshooting
ms.assetid: bb3d3322-0e5e-4dd5-b93a-24d5fbcd2ffd
caps.latest.revision: 29
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: a1ddf51d02d9e20f6806f8bc202f8a08166876d6
ms.contentlocale: es-es
ms.lasthandoff: 09/26/2017

---
# <a name="how-to-use-the-activity-log"></a>Cómo: usar el registro de actividad
VSPackages puede escribir mensajes en el registro de actividad. Esta característica es especialmente útil para depurar los VSPackages en entornos de venta directa.  
  
> [!TIP]
>  El registro de actividad está siempre activado. Visual Studio mantiene un búfer gradual de las entradas de la última cien, así como las diez primeras entradas, que tienen información de configuración general.  
  
### <a name="to-write-an-entry-to-the-activity-log"></a>Para escribir una entrada en el registro de actividad  
  
1.  Inserte este código en el <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> método o en cualquier otro método excepto en el constructor de VSPackage:  
  
    ```csharp  
    IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (log == null) return;  
  
    int hr = log.LogEntry((UInt32)__ACTIVITYLOG_ENTRYTYPE.ALE_INFORMATION,  
        this.ToString(),  
        string.Format(CultureInfo.CurrentCulture,  
        "Called for: {0}", this.ToString()));  
    ```  
  
     Este código obtiene la <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> de servicio y lo convierte a un <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interfaz. <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A>escribe una entrada informativa en el registro de actividad utilizando el contexto de la referencia cultural actual.  
  
2.  Cuando se carga el VSPackage (normalmente, cuando se invoca un comando o se abre una ventana), el texto se escribe en el registro de actividad.  
  
### <a name="to-examine-the-activity-log"></a>Para examinar el registro de actividad  
  
1.  Buscar el registro de actividad en la subcarpeta para los datos de Visual Studio: *% AppData %*\Microsoft\VisualStudio\15.0\ActivityLog.XML...  
  
2.  Abra el registro de actividad con cualquier editor de texto. Esta es una entrada típica:  
  
    ```  
    Called for: Company.MyApp.MyAppPackage ...  
    ```  
  
## <a name="robust-programming"></a>Programación sólida  
 Dado que el registro de actividad es un servicio, el registro de actividad no está disponible en el constructor de VSPackage.  
  
 Debe obtener el registro de actividad justo antes de escribir en él. No almacenar en memoria caché o guardar el registro de actividad para un uso futuro.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE>   
 [Solucionar problemas de VSPackages](../extensibility/troubleshooting-vspackages.md)   
 [VSPackages](../extensibility/internals/vspackages.md)

