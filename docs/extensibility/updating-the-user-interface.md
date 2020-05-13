---
title: Actualización de la interfaz de usuario ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, updating
- commands, updating UI
ms.assetid: 376e2f56-e7bf-4e62-89f5-3dada84a404b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1c51ae790eb35645fbe9aec5d9c422e1051aaa69
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698882"
---
# <a name="updating-the-user-interface"></a>Actualización de la interfaz de usuario
Después de implementar un comando, puede agregar código para actualizar la interfaz de usuario con el estado de los nuevos comandos.

 En una aplicación Típica de Win32, el conjunto de comandos se puede sondear continuamente y el estado de los comandos individuales se puede ajustar a medida que el usuario los ve. Sin embargo, dado que el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] shell puede hospedar un número ilimitado de VSPackages, el sondeo extenso puede disminuir la capacidad de respuesta, especialmente el sondeo entre ensamblados de interoperabilidad entre código administrado y COM.

### <a name="to-update-the-ui"></a>Para actualizar la interfaz de usuario

1. Realice uno de estos pasos:

    - Llame al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> .

         Una <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interfaz se puede <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> obtener del servicio, de la siguiente manera.

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

         Si el parámetro <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> de la`TRUE`es distinto de cero ( ), entonces la actualización se realiza de forma sincrónica e inmediatamente. Se recomienda pasar cero`FALSE`( ) para este parámetro para ayudar a mantener un buen rendimiento. Si desea evitar el almacenamiento `DontCache` en caché, aplique la marca al crear el comando en el archivo .vsct. Sin embargo, utilice la bandera con precaución o el rendimiento podría disminuir. Para obtener más información acerca de los indicadores de comando, consulte la documentación del [elemento Command Flag.](../extensibility/command-flag-element.md)

    - En VSPackages que hospedan un control ActiveX mediante el modelo de activación en <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> contexto en una ventana, podría ser más conveniente usar el método. El <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> método <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> en la <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> y el método en la interfaz son funcionalmente equivalentes. Ambos hacen que el entorno vuelva a consultar el estado de todos los comandos. Normalmente, una actualización no se realiza inmediatamente. En su lugar, una actualización se retrasa hasta el tiempo de inactividad. El shell almacena en caché el estado del comando para ayudar a mantener un buen rendimiento. Si desea evitar el almacenamiento `DontCache` en caché, aplique la marca al crear el comando en el archivo .vsct. Sin embargo, utilice el indicador con precaución porque el rendimiento podría disminuir.

         Tenga en cuenta <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> que puede `QueryInterface` obtener la <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager> interfaz llamando al método <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> en un objeto o obteniendo la interfaz del servicio.

## <a name="see-also"></a>Vea también
- [Cómo VSPackages agrega elementos de la interfaz de usuario](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Implementación](../extensibility/internals/command-implementation.md)
