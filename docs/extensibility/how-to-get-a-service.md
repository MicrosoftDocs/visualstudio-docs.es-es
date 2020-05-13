---
title: 'Cómo: Obtener un servicio ? Microsoft Docs'
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- services, consuming
ms.assetid: 1f000020-8fb7-4e39-8e1e-2e38c7fec3d4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e8e6f20eaa08d6bb7aaa0cc9e560856daa5959e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710954"
---
# <a name="how-to-get-a-service"></a>Cómo: Obtener un servicio

A menudo necesita obtener servicios de Visual Studio para tener acceso a diferentes características. En general, un servicio de Visual Studio proporciona una o varias interfaces que puede usar. Puede obtener la mayoría de los servicios de un VSPackage.

Cualquier VSPackage que <xref:Microsoft.VisualStudio.Shell.Package> deriva y que se ha colocado correctamente puede solicitar cualquier servicio global. Dado `Package` que la <xref:System.IServiceProvider>clase implementa , cualquier `Package` VSPackage que deriva también es un proveedor de servicios.

Cuando Visual Studio <xref:Microsoft.VisualStudio.Shell.Package>carga un <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> , pasa <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> un objeto al método durante la inicialización. Esto se denomina *sentar* el VSPackage. La `Package` clase ajusta este proveedor <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> de servicios y proporciona el método para obtener servicios.

## <a name="getting-a-service-from-an-initialized-vspackage"></a>Obtener un servicio de un VSPackage inicializado

1. Cada extensión de Visual Studio comienza con un proyecto de implementación de VSIX, que contendrá los activos de extensión. Cree [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] un proyecto `GetServiceExtension`VSIX denominado . Puede encontrar la plantilla de proyecto VSIX en el cuadro de diálogo **Nuevo proyecto** buscando "vsix".

2. Ahora agregue una plantilla de elemento de comando personalizada denominada **GetServiceCommand**. En el cuadro de diálogo **Agregar nuevo elemento** , vaya a**Extensibilidad** de **Visual C-** > y seleccione **Comando personalizado**. En el campo **Nombre** en la parte inferior de la ventana, cambie el nombre del archivo de comandos a *GetServiceCommand.cs*. Para obtener más información acerca de cómo crear un comando personalizado, [Crear una extensión con un comando](../extensibility/creating-an-extension-with-a-menu-command.md) de menú

3. En *GetServiceCommand.cs*, quite `MenuItemCommand` el cuerpo del método y agregue el código siguiente:

   ```csharp
   IVsActivityLog activityLog = ServiceProvider.GetService(typeof(SVsActivityLog)) as IVsActivityLog;
   if (activityLog == null) return;
   System.Windows.Forms.MessageBox.Show("Found the activity log service.");

   ```

    Este código obtiene un servicio SVsActivityLog y <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> lo convierte en una interfaz, que se puede usar para escribir en el registro de actividad. Para obtener un ejemplo, consulte [Cómo: Usar el registro](../extensibility/how-to-use-the-activity-log.md)de actividad .

4. Compile la solución y comience la depuración. Aparece la instancia experimental.

5. En el menú **Herramientas** de la instancia experimental, busque el botón **Invocar GetServiceCommand.** Al hacer clic en este botón, debería ver un cuadro de mensaje que dice Encontrado el servicio de registro de **actividad.**

## <a name="getting-a-service-from-a-tool-window-or-control-container"></a>Obtener un servicio desde una ventana de herramientas o un contenedor de control

A veces es posible que necesite obtener un servicio desde una ventana de herramientas o un contenedor de control que no se ha ubicado, o bien se ha ubicado con un proveedor de servicios que no conoce el servicio que desea. Por ejemplo, es posible que desee escribir en el registro de actividad desde dentro de un control.

El <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> método estático se basa en un proveedor de servicios en caché <xref:Microsoft.VisualStudio.Shell.Package> que se inicializa la primera vez que se encuentra cualquier VSPackage derivado de.

Dado que el VSPackage se llama antes de que el VSPackage está sitio, los servicios globales normalmente no están disponibles desde dentro del constructor de VSPackage. Consulte [Cómo: Solucionar problemas de servicios](../extensibility/how-to-troubleshoot-services.md) para obtener una solución alternativa.

Este es un ejemplo de la forma de obtener un servicio en una ventana de herramientas u otro elemento que no sea VSPackage.

```csharp
IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;
if (log == null) return;
```

## <a name="getting-a-service-from-the-dte-object"></a>Obtener un servicio desde el objeto DTE

También puede obtener <xref:EnvDTE.DTEClass> servicios de objeto. Sin embargo, debe obtener el objeto DTE como un <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> servicio de un VSPackage o mediante una llamada al método estático.

El objeto DTE <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>implementa, que puede usar para <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A>consultar un servicio mediante .

A continuación se muestra cómo obtener un servicio desde el objeto DTE.

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

- [Cómo: Proporcionar un servicio](../extensibility/how-to-provide-a-service.md)
- [Usar y proporcionar servicios](../extensibility/using-and-providing-services.md)
- [Elementos esenciales del servicio](../extensibility/internals/service-essentials.md)
