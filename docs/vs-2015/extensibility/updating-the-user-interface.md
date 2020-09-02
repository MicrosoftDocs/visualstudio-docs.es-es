---
title: Actualizando la interfaz de usuario | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, updating
- commands, updating UI
ms.assetid: 376e2f56-e7bf-4e62-89f5-3dada84a404b
caps.latest.revision: 42
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: db5be965119d1564f2a4bf8a15892af7142663e0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186357"
---
# <a name="updating-the-user-interface"></a>Actualización de la interfaz de usuario
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Después de implementar un comando, puede agregar código para actualizar la interfaz de usuario con el estado de los nuevos comandos.  
  
 En una aplicación típica de Win32, el conjunto de comandos se puede sondear continuamente y el estado de los comandos individuales se puede ajustar a medida que el usuario los ve. Sin embargo, dado [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] que el shell puede hospedar un número ilimitado de VSPackages, un sondeo extensivo podría reducir la capacidad de respuesta, especialmente el sondeo entre ensamblados de interoperabilidad entre el código administrado y com.  
  
### <a name="to-update-the-ui"></a>Para actualizar la interfaz de usuario  
  
1. Realice uno de estos pasos:  
  
    - Llame al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> .  
  
         Una <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interfaz se puede obtener del <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> servicio, como se indica a continuación.  
  
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
  
         Si el parámetro de <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> es distinto de cero ( `TRUE` ), la actualización se realiza de forma sincrónica y inmediata. Se recomienda pasar cero ( `FALSE` ) para este parámetro a fin de ayudar a mantener un buen rendimiento. Si desea evitar el almacenamiento en caché, aplique la `DontCache` marca al crear el comando en el archivo. Vsct. No obstante, use la marca con precaución o el rendimiento podría disminuir. Para obtener más información sobre las marcas de comandos, consulte la documentación del elemento de la [marca de comandos](../extensibility/command-flag-element.md) .  
  
    - En los paquetes VSPackage que hospedan un control ActiveX mediante el modelo de activación en contexto en una ventana, podría ser más conveniente utilizar el <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> método. El <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> método de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interfaz y el <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> método de la <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> interfaz son funcionalmente equivalentes. Ambos hacen que el entorno vuelva a consultar el estado de todos los comandos. Normalmente, una actualización no se realiza inmediatamente. En su lugar, se retrasa una actualización hasta el tiempo de inactividad. El shell almacena en caché el estado del comando para ayudar a mantener un buen rendimiento. Si desea evitar el almacenamiento en caché, aplique la `DontCache` marca al crear el comando en el archivo. Vsct. No obstante, use la marca con precaución porque el rendimiento podría disminuir.  
  
         Tenga en cuenta que puede obtener la <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> interfaz llamando al `QueryInterface` método en un <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager> objeto o obteniendo la interfaz desde el <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> servicio.  
  
## <a name="see-also"></a>Consulte también  
 [Cómo agrega VSPackages los elementos de la interfaz de usuario](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Implementación](../extensibility/internals/command-implementation.md)
