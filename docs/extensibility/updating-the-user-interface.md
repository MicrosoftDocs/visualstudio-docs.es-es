---
title: Actualizando la interfaz de usuario | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, updating
- commands, updating UI
ms.assetid: 376e2f56-e7bf-4e62-89f5-3dada84a404b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6b3bc8c4b87aefe62cbd27e64fc426ddb7abf96e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="updating-the-user-interface"></a>Actualización de la interfaz de usuario
Después de implementar un comando, puede agregar código para actualizar la interfaz de usuario con el estado de los comandos de nuevo.  
  
 En una aplicación típica de Win32, el conjunto de comandos que se puede sondear continuamente y se puede ajustar el estado de comandos individuales tal y como el usuario ve ellos. Sin embargo, dado que el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] shell puede hospedar un número ilimitado de VSPackages, una amplia sondeo puede reducir la capacidad de respuesta, especialmente de sondeo en los ensamblados de interoperabilidad entre código administrado y COM.  
  
### <a name="to-update-the-ui"></a>Para actualizar la interfaz de usuario  
  
1.  Realice uno de estos pasos:  
  
    -   Llame al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A>.  
  
         Un <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interfaz puede obtenerse de la <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> de servicio, como se indica a continuación.  
  
        ```csharp  
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
  
         Si el parámetro de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> es distinto de cero (`TRUE`), se llevará a cabo la actualización de forma sincrónica e inmediatamente. Se recomienda pasar cero (`FALSE`) para este parámetro ayudar a mantener un buen rendimiento. Si desea evitar el almacenamiento en caché, se aplican los `DontCache` marca cuando se crea el comando en el archivo .vsct. No obstante, use la marca con precaución o puede reducir el rendimiento. Para obtener más información acerca de las marcas de comando, consulte el [comando marca elemento](../extensibility/command-flag-element.md) documentación.  
  
    -   En los paquetes VSPackage que hospedar un control ActiveX mediante el modelo de activación en contexto en una ventana, puede que sea más conveniente utilizar el <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> método. El <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> método en el <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interfaz y la <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> método en el <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> interfaz son funcionalmente equivalentes. Ambas hacen que el entorno volver a consultar el estado de todos los comandos. Por lo general, una actualización no se realiza de forma inmediata. En su lugar, una actualización se retrasa hasta el tiempo de inactividad. El shell se almacena en memoria caché el estado del comando para ayudar a mantener un buen rendimiento. Si desea evitar el almacenamiento en caché, se aplican los `DontCache` marca cuando se crea el comando en el archivo .vsct. No obstante, use la marca con precaución porque podría reducir el rendimiento.  
  
         Tenga en cuenta que puede obtener la <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> interfaz mediante una llamada a la `QueryInterface` método en un <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager> objeto u obtenido mediante la interfaz de la <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> servicio.  
  
## <a name="see-also"></a>Vea también  
 [¿Cómo VSPackages agregar elementos de la interfaz de usuario](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Implementación](../extensibility/internals/command-implementation.md)