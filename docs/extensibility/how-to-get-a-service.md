---
title: 'Cómo: obtener un servicio | Microsoft Docs'
description: Obtenga información sobre cómo obtener servicios de Visual Studio para tener acceso a distintas características. Puede obtener la mayoría de los servicios mediante un VSPackage.
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- services, consuming
ms.assetid: 1f000020-8fb7-4e39-8e1e-2e38c7fec3d4
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d60e6093eb439aa3b0e2a0a86e0d21d8ace95e00
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99911749"
---
# <a name="how-to-get-a-service"></a>Cómo: obtener un servicio

A menudo es necesario obtener los servicios de Visual Studio para tener acceso a distintas características. En general, un servicio de Visual Studio proporciona una o más interfaces que puede usar. Puede obtener la mayoría de los servicios de un VSPackage.

Cualquier VSPackage que se derive de <xref:Microsoft.VisualStudio.Shell.Package> y que se haya puesto en sitio correctamente puede solicitar cualquier servicio global. Dado `Package` que la clase implementa <xref:System.IServiceProvider> , cualquier VSPackage derivado de `Package` también es un proveedor de servicios.

Cuando Visual Studio carga una <xref:Microsoft.VisualStudio.Shell.Package> , pasa un <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> objeto al <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> método durante la inicialización. Esto se denomina *emplazamiento* del VSPackage. La `Package` clase contiene este proveedor de servicios y proporciona el <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> método para obtener servicios.

## <a name="getting-a-service-from-an-initialized-vspackage"></a>Obtener un servicio de un VSPackage inicializado

1. Cada extensión de Visual Studio comienza con un proyecto de implementación de VSIX, que contendrá los recursos de la extensión. Cree un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Proyecto VSIX denominado `GetServiceExtension` . Para buscar la plantilla de Proyecto VSIX en el cuadro de diálogo **nuevo proyecto** , busque "VSIX".

2. Ahora, agregue una plantilla de elemento de comando personalizada denominada **GetServiceCommand**. En el cuadro de diálogo **Agregar nuevo elemento** , vaya a extensibilidad de **Visual C#**  >   y seleccione **comando personalizado**. En el campo **nombre** situado en la parte inferior de la ventana, cambie el nombre del archivo de comandos a *GetServiceCommand.CS*. Para obtener más información sobre cómo crear un comando personalizado, [cree una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md) .

3. En *GetServiceCommand.CS*, quite el cuerpo del `MenuItemCommand` método y agregue el código siguiente:

   ```csharp
   IVsActivityLog activityLog = ServiceProvider.GetService(typeof(SVsActivityLog)) as IVsActivityLog;
   if (activityLog == null) return;
   System.Windows.Forms.MessageBox.Show("Found the activity log service.");

   ```

    Este código obtiene un servicio SVsActivityLog y lo convierte en una <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interfaz, que se puede usar para escribir en el registro de actividad. Para obtener un ejemplo, consulte [Cómo: usar el registro de actividad](../extensibility/how-to-use-the-activity-log.md).

4. Compile la solución y comience la depuración. Aparece la instancia experimental.

5. En el menú **herramientas** de la instancia experimental, busque el botón **invocar GetServiceCommand** . Al hacer clic en este botón, debería ver un cuadro de mensaje que indica que **se encontró el servicio de registro de actividad.**

## <a name="getting-a-service-from-a-tool-window-or-control-container"></a>Obtener un servicio desde una ventana de herramientas o un contenedor de controles

En ocasiones, es posible que necesite obtener un servicio desde una ventana de herramientas o un contenedor de controles que no se haya puesto en el sitio, o bien que se haya puesto en un proveedor de servicios que no conozca el servicio que desea. Por ejemplo, puede que desee escribir en el registro de actividad desde un control.

El método estático se <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> basa en un proveedor de servicios almacenado en memoria caché que se inicializa la primera vez que se sitúa en el sitio un VSPackage derivado de <xref:Microsoft.VisualStudio.Shell.Package> .

Dado que se llama al constructor VSPackage antes de que el VSPackage esté en el sitio, los servicios globales normalmente no están disponibles desde el constructor VSPackage. Consulte [Cómo: solucionar problemas](../extensibility/how-to-troubleshoot-services.md) de los servicios para obtener una solución alternativa.

Este es un ejemplo de la forma de obtener un servicio en una ventana de herramientas o en otro elemento que no es de VSPackage.

```csharp
IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;
if (log == null) return;
```

## <a name="getting-a-service-from-the-dte-object"></a>Obtener un servicio del objeto DTE

También puede obtener servicios del <xref:EnvDTE.DTEClass> objeto. Sin embargo, debe obtener el objeto DTE como un servicio de un VSPackage o llamando al método estático <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> .

El objeto DTE implementa <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> , que puede usar para consultar un servicio mediante <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> .

Aquí se muestra cómo obtener un servicio desde el objeto DTE.

```csharp
// Start with the DTE object, for example: 
// using EnvDTE;
// DTE dte = (DTE)GetService(typeof(DTE));

ServiceProvider sp = new ServiceProvider((Microsoft.VisualStudio.OLE.Interop.IServiceProvider)dte);
if (sp != null)
{
    IVsActivityLog log = sp.GetService(typeof(SVsActivityLog)) as IVsActivityLog;
    if (log != null)
    {
        System.Windows.Forms.MessageBox.Show("Found the activity log service.");
    }
}
```

## <a name="see-also"></a>Vea también

- [Cómo: proporcionar un servicio](../extensibility/how-to-provide-a-service.md)
- [Usar y proporcionar servicios](../extensibility/using-and-providing-services.md)
- [Aspectos básicos del servicio](../extensibility/internals/service-essentials.md)
