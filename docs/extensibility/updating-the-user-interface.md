---
title: "Actualizaci&#243;n de la interfaz de usuario | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "interfaces de usuario, actualizar"
  - "comandos, actualizar la interfaz de usuario"
ms.assetid: 376e2f56-e7bf-4e62-89f5-3dada84a404b
caps.latest.revision: 41
caps.handback.revision: 41
ms.author: "gregvanl"
manager: "ghogen"
---
# Actualizaci&#243;n de la interfaz de usuario
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Después de implementar un comando, puede agregar código para actualizar la interfaz de usuario con el estado de los comandos de nuevo.  
  
 En una aplicación típica de Win32, el conjunto de comandos que se puede sondear continuamente y se puede ajustar el estado de comandos individuales que ve el usuario. Sin embargo, dado que el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] shell puede hospedar un número ilimitado de VSPackages, sondeo extenso podría disminuir la capacidad de respuesta, especialmente de sondeo en los ensamblados de interoperabilidad entre código administrado y COM.  
  
### Para actualizar la interfaz de usuario  
  
1.  Realice uno de estos pasos:  
  
    -   Llame al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A>.  
  
         Un <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interfaz puede obtenerse desde el <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> del servicio, como sigue.  
  
        ```c#  
        void UpdateUI(Microsoft.VisualStudio.Shell.ServiceProvider sp)  
        {  
            IVsUIShell vsShell = (IVsUIShell)sp.GetService(typeof(IVsUIShell));  
            if (vsShell != null)  
            {  
                int hr = vsShell.UpdateCommandUI(0);  
                Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(hr);  
            }  
        }  
  
        ```  
  
         Si el parámetro de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> es distinto de cero \(`TRUE`\), a continuación, la actualización se realiza sincrónicamente e inmediatamente. Se recomienda pasar cero \(`FALSE`\) para este parámetro ayudar a mantener un buen rendimiento. Si desea evitar el almacenamiento en caché, se aplican los `DontCache` marca al crear el comando en el archivo .vsct. No obstante, utilice el indicador con precaución o es posible que disminuya el rendimiento. Para obtener más información acerca de los indicadores de comando, consulte el [Elemento de indicador de comando](../extensibility/command-flag-element.md) documentación.  
  
    -   En VSPackages que hospedar un control ActiveX mediante el modelo de activación en contexto en una ventana, puede ser más conveniente utilizar el <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> método. El <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> método en el <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interfaz y <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> método en el <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> interfaz son funcionalmente equivalentes. Ambas hacen que el entorno volver a consultar el estado de todos los comandos. Normalmente, una actualización no se realiza inmediatamente. En su lugar, una actualización se retrasa hasta el tiempo de inactividad. El shell se almacena en caché el estado de comandos para ayudar a mantener un buen rendimiento. Si desea evitar el almacenamiento en caché, se aplican los `DontCache` marca al crear el comando en el archivo .vsct. No obstante, utilice el indicador con precaución porque podría disminuir el rendimiento.  
  
         Tenga en cuenta que puede obtener el <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> interfaz llamando el `QueryInterface` método en un <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager> de objeto u obteniendo la interfaz de la <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> servicio.  
  
## Vea también  
 [Cómo VSPackages agregar elementos de la interfaz de usuario](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Implementación](../extensibility/internals/command-implementation.md)