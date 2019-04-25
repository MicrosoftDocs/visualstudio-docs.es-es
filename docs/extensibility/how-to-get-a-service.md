---
title: Filtrar Obtener un servicio | Documentos de Microsoft
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- services, consuming
ms.assetid: 1f000020-8fb7-4e39-8e1e-2e38c7fec3d4
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 027057ff5c6f8d33038329a8e6029dcb4eeac477
ms.sourcegitcommit: 4d9c54f689416bf1dc4ace058919592482d02e36
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58194313"
---
# <a name="how-to-get-a-service"></a>Filtrar Obtener un servicio

A menudo necesitará obtener servicios de Visual Studio para tener acceso a características diferentes. En general, un servicio de Visual Studio proporciona una o más interfaces que puede usar. Puede obtener la mayoría de los servicios desde un VSPackage.

Cualquier VSPackage que se derive de <xref:Microsoft.VisualStudio.Shell.Package> y que se ha ubicado correctamente puede pedir a cualquier servicio global. Dado que el `Package` la clase implementa <xref:System.IServiceProvider>, cualquier VSPackage que se derive de `Package` también es un proveedor de servicios.

Cuando Visual Studio carga un <xref:Microsoft.VisualStudio.Shell.Package>, pasa una <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> de objeto para el <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> método durante la inicialización. Esto se denomina *situación* el VSPackage. El `Package` clase ajusta este proveedor de servicios y proporciona el <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> método para obtener servicios.

## <a name="getting-a-service-from-an-initialized-vspackage"></a>Obtención de un servicio de un VSPackage inicializado

1. Todas las extensiones de Visual Studio se inicia con un proyecto de implementación VSIX, que contendrá los recursos de extensión. Crear un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] proyecto VSIX denominado `GetServiceExtension`. Puede encontrar la plantilla de proyecto VSIX en el **nuevo proyecto** diálogo buscando "vsix".

2. Ahora agregue una plantilla de elemento de comando personalizado denominada **GetServiceCommand**. En el **Agregar nuevo elemento** cuadro de diálogo, vaya a **Visual C#** > **extensibilidad** y seleccione **comando personalizado**. En el **nombre** campo en la parte inferior de la ventana, cambie el nombre de archivo de comandos para *GetServiceCommand.cs*. Para obtener más información sobre cómo crear un comando personalizado, [crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md)

3. En *GetServiceCommand.cs*, quite el cuerpo de la `MenuItemCommand` método y agregue el código siguiente:

   ```csharp
   IVsActivityLog activityLog = ServiceProvider.GetService(typeof(SVsActivityLog)) as IVsActivityLog;
   if (activityLog == null) return;
   System.Windows.Forms.MessageBox.Show("Found the activity log service.");

   ```

    Este código obtiene un servicio SVsActivityLog y lo convierte a un <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interfaz, que puede usarse para escribir en el registro de actividad. Como ejemplo, vea [Cómo: Usar el registro de actividad](../extensibility/how-to-use-the-activity-log.md).

4. Compile la solución y comience la depuración. Aparece la instancia experimental.

5. En el **herramientas** Buscar del menú de la instancia experimental, el **GetServiceCommand invocar** botón. Al hacer clic en este botón, debería ver un cuadro de mensaje que dice **se encuentra el servicio de registro de actividad.**

## <a name="getting-a-service-from-a-tool-window-or-control-container"></a>Obtención de un servicio de un contenedor de control o ventana de herramientas

A veces es posible que necesita obtener un servicio de una ventana de herramientas o control contenedor que no se ha ubicado, o bien que se ha ubicado con un proveedor de servicios que no conoce el servicio que desee. Por ejemplo, puede escribir en el registro de actividad desde dentro de un control.

Estático <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> método se basa en un proveedor de servicios en caché que se inicializa la primera vez que se deriva de cualquier VSPackage <xref:Microsoft.VisualStudio.Shell.Package> está situado.

Dado que se llama al constructor de VSPackage antes de que se basa en un VSPackage, servicios globales son normalmente no está disponibles desde dentro del constructor de VSPackage. Vea [Cómo: Solucionar problemas de servicios](../extensibility/how-to-troubleshoot-services.md) para encontrar una solución.

Este es un ejemplo de la forma de obtener un servicio en una ventana de herramientas o en otro elemento que no sean VSPackage.

```csharp
IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;
if (log == null) return;
```

## <a name="getting-a-service-from-the-dte-object"></a>Obtención de un servicio del objeto DTE

También puede obtener servicios de <xref:EnvDTE.DTEClass> objeto. Sin embargo, debe obtener el objeto DTE como un servicio desde un VSPackage, o mediante una llamada a estático <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> método.

Implementa el objeto DTE <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>, que puede usar para consultar un servicio mediante el uso de <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A>.

Aquí le mostramos cómo obtener un servicio del objeto DTE.

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
- [Usar y proporcionan servicios](../extensibility/using-and-providing-services.md)
- [Conceptos básicos del servicio](../extensibility/internals/service-essentials.md)