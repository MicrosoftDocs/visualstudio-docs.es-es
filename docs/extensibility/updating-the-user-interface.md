---
title: Actualizando la interfaz de usuario | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, updating
- commands, updating UI
ms.assetid: 376e2f56-e7bf-4e62-89f5-3dada84a404b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bf41a41e68aa73e07bdcafe8bcdcd335fff6e6eb
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72718785"
---
# <a name="updating-the-user-interface"></a>Actualización de la interfaz de usuario
Después de implementar un comando, puede agregar código para actualizar la interfaz de usuario con el estado de los nuevos comandos.

 En una aplicación típica de Win32, el conjunto de comandos se puede sondear continuamente y el estado de los comandos individuales se puede ajustar a medida que el usuario los ve. Sin embargo, dado que el shell de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] puede hospedar un número ilimitado de paquetes de paquetes de VSPackages, el sondeo extenso puede reducir la capacidad de respuesta, especialmente el sondeo entre ensamblados de interoperabilidad entre el código administrado y COM.

### <a name="to-update-the-ui"></a>Para actualizar la interfaz de usuario

1. Realice uno de estos pasos:

    - Llame al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A>.

         Se puede obtener una interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> del servicio <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>, como se indica a continuación.

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

         Si el parámetro del <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> es distinto de cero (`TRUE`), la actualización se realiza de forma sincrónica y inmediata. Se recomienda pasar cero (`FALSE`) para este parámetro con el fin de ayudar a mantener un buen rendimiento. Si desea evitar el almacenamiento en caché, aplique la marca `DontCache` al crear el comando en el archivo. Vsct. No obstante, use la marca con precaución o el rendimiento podría disminuir. Para obtener más información sobre las marcas de comandos, consulte la documentación del elemento de la [marca de comandos](../extensibility/command-flag-element.md) .

    - En los paquetes VSPackage que hospedan un control ActiveX mediante el modelo de activación en contexto en una ventana, podría ser más conveniente utilizar el método <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A>. El método <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> de la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> y el método <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> de la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> son funcionalmente equivalentes. Ambos hacen que el entorno vuelva a consultar el estado de todos los comandos. Normalmente, una actualización no se realiza inmediatamente. En su lugar, se retrasa una actualización hasta el tiempo de inactividad. El shell almacena en caché el estado del comando para ayudar a mantener un buen rendimiento. Si desea evitar el almacenamiento en caché, aplique la marca `DontCache` al crear el comando en el archivo. Vsct. No obstante, use la marca con precaución porque el rendimiento podría disminuir.

         Tenga en cuenta que puede obtener la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> llamando al método `QueryInterface` en un objeto <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager> o obteniendo la interfaz del servicio <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager>.

## <a name="see-also"></a>Vea también
- [Adición de elementos de la interfaz de usuario por VSPackages](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Implementación](../extensibility/internals/command-implementation.md)