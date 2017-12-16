---
title: "Cómo: obtener un servicio | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: services, consuming
ms.assetid: 1f000020-8fb7-4e39-8e1e-2e38c7fec3d4
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: dc427dbca201b472feca89201284ab009abd9d34
ms.sourcegitcommit: f36eb7f989efbdbed0d0a087afea8ffe27d8ca15
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/14/2017
---
# <a name="how-to-get-a-service"></a>Cómo: obtener un servicio
A menudo necesitará obtener servicios de Visual Studio para tener acceso a características diferentes. En general, un servicio de Visual Studio proporciona una o varias interfaces que puede usar. Puede obtener la mayoría de los servicios de un VSPackage.  
  
 Cualquier paquete de VS que se deriva de <xref:Microsoft.VisualStudio.Shell.Package> y que se ha ubicado correctamente puede pedir cualquier servicio global. Dado que implementa la clase de paquete <xref:System.IServiceProvider>, cualquier paquete de VS que se deriva de paquete también es un proveedor de servicios.  
  
 Cuando Visual Studio carga un <xref:Microsoft.VisualStudio.Shell.Package>, pasa una <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> el objeto a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> método durante la inicialización. Esto se denomina *situación* el VSPackage. La clase de paquete ajusta este proveedor de servicios y proporciona el <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> método para obtener servicios.  
  
## <a name="getting-a-service-from-an-initialized-vspackage"></a>Obtener un servicio de un VSPackage inicializado  
  
1.  Cada extensión de Visual Studio se inicia con un proyecto de implementación de VSIX que contendrá los activos de la extensión. Crear un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] proyecto VSIX denominado `GetServiceExtension`. Puede encontrar la plantilla de proyecto VSIX en la **nuevo proyecto** en el cuadro de diálogo **Visual C# > extensibilidad**.  
  
2.  Ahora agregue una plantilla de elemento de comando personalizado denominada **GetServiceCommand**. En el **Agregar nuevo elemento** cuadro de diálogo, vaya a **Visual C# > extensibilidad** y seleccione **comando personalizado**. En el **nombre** campo en la parte inferior de la ventana, cambie el nombre de archivo de comandos para **GetServiceCommand.cs**. Para obtener más información sobre cómo crear un comando personalizado, [crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
3.  En GetServiceCommand.cs, quite el cuerpo del método MenuItemCommand y agregue el código siguiente:  
  
    ```csharp  
    IVsActivityLog activityLog = ServiceProvider.GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (activityLog == null) return;  
    System.Windows.Forms.MessageBox.Show("Found the activity log service.");  
  
    ```  
  
     Este código obtiene un servicio SVsActivityLog y lo convierte a un <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interfaz, que se puede usar para escribir en el registro de actividad. Para obtener un ejemplo, vea [Cómo: usar el registro de actividad](../extensibility/how-to-use-the-activity-log.md).  
  
4.  Compile la solución y comience la depuración. Aparece la instancia experimental.  
  
5.  En el menú Herramientas de la instancia experimental, busque el **GetServiceCommand invocar** botón. Al hacer clic en este botón, debería ver un cuadro de mensaje que indicara **encuentra el servicio de registro de actividad.**  
  
## <a name="getting-a-service-from-a-tool-window-or-control-container"></a>Obtener un servicio de un contenedor de control o la ventana de herramienta  
 A veces, debe obtener un servicio desde una ventana de herramientas o control contenedor que no se ha ubicado, o bien se ha ubicado en un sitio con un proveedor de servicios que no conozca el servicio que desee. Por ejemplo, puede escribir en el registro de actividad desde dentro de un control.  
  
 El método estático <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> método se basa en un proveedor de servicio almacenado en caché que se inicializa la primera vez que se deriva de cualquier VSPackage <xref:Microsoft.VisualStudio.Shell.Package> sitúa.  
  
 Dado que se llama al constructor de VSPackage antes de que se basa en un VSPackage, servicios globales son normalmente no está disponibles desde dentro del constructor de VSPackage. Vea [Cómo: solucionar problemas de servicios](../extensibility/how-to-troubleshoot-services.md) para encontrar una solución.  
  
 Este es un ejemplo de la manera de obtener un servicio en una ventana de herramientas u otro elemento no VSPackage.  
  
```csharp  
IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;  
if (log == null) return;  
```  
  
## <a name="getting-a-service-from-the-dte-object"></a>Obtener un servicio del objeto DTE  
 También puede obtener servicios de <xref:EnvDTE.DTEClass> objeto. Sin embargo, debe obtener el objeto DTE como un servicio de un paquete VSPackage o mediante una llamada a estático <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> método.  
  
 Implementa el objeto DTE <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>, que puede usar para consultar un servicio mediante <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A>.  
  
 Aquí se muestra cómo obtener un servicio del objeto DTE.  
  
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
 [Cómo: proporcionar un servicio](../extensibility/how-to-provide-a-service.md)   
 [Uso y proporciona servicios](../extensibility/using-and-providing-services.md)   
 [Conceptos básicos del servicio](../extensibility/internals/service-essentials.md)