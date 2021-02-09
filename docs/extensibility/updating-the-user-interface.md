---
title: Actualizando la interfaz de usuario | Microsoft Docs
description: Obtenga información sobre cómo agregar código para actualizar la interfaz de usuario después de implementar un nuevo comando en el VSPackage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, updating
- commands, updating UI
ms.assetid: 376e2f56-e7bf-4e62-89f5-3dada84a404b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fd088d6887e7c7b60ea5a4101de050149583c5a2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893456"
---
# <a name="updating-the-user-interface"></a>Actualización de la interfaz de usuario
Después de implementar un comando, puede agregar código para actualizar la interfaz de usuario con el estado de los nuevos comandos.

 En una aplicación típica de Win32, el conjunto de comandos se puede sondear continuamente y el estado de los comandos individuales se puede ajustar a medida que el usuario los ve. Sin embargo, dado [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que el shell puede hospedar un número ilimitado de VSPackages, un sondeo extensivo podría reducir la capacidad de respuesta, especialmente el sondeo entre ensamblados de interoperabilidad entre el código administrado y com.

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

## <a name="see-also"></a>Vea también
- [Cómo VSPackages agrega elementos de la interfaz de usuario](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Implementación](../extensibility/internals/command-implementation.md)
