---
title: "C&#243;mo: obtener un servicio | Microsoft Docs"
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
  - "Servicios de consumo"
ms.assetid: 1f000020-8fb7-4e39-8e1e-2e38c7fec3d4
caps.latest.revision: 20
caps.handback.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
---
# C&#243;mo: obtener un servicio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A menudo necesitará obtener servicios de Visual Studio para tener acceso a características diferentes. En general, un servicio de Visual Studio proporciona una o más interfaces que puede utilizar. Puede obtener la mayoría de los servicios de un VSPackage.  
  
 Cualquier paquete VSPackage que se deriva de <xref:Microsoft.VisualStudio.Shell.Package> y que se ha ubicado correctamente puede solicitar cualquier servicio global. Dado que implementa la clase de paquete <xref:System.IServiceProvider>, cualquier paquete VSPackage que se deriva de paquete también es un proveedor de servicios.  
  
 Cuando Visual Studio carga un <xref:Microsoft.VisualStudio.Shell.Package>, pasa una <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> de objeto para el <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> durante la inicialización. Esto se denomina *situación* VSPackage. La clase de paquete ajusta este proveedor de servicios y proporciona el <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> método para obtener servicios.  
  
## Obtención de un servicio de un VSPackage inicializado  
  
1.  Todas las extensiones de Visual Studio se inicia con un proyecto de implementación de VSIX que contiene los activos de la extensión. Crear un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] proyecto VSIX denominado `GetServiceExtension`. Puede encontrar la plantilla de proyecto VSIX en la **nuevo proyecto** en el cuadro de diálogo **Visual C\# \/ extensibilidad**.  
  
2.  Ahora agregue una plantilla de elemento de comando personalizado denominada **GetServiceCommand**. En el **Agregar nuevo elemento** cuadro de diálogo, vaya a **Visual C\# \/ extensibilidad** y seleccione **comando personalizado**. En el **nombre** campo en la parte inferior de la ventana, el nombre del archivo de comandos **GetServiceCommand.cs**. Para obtener más información sobre cómo crear un comando personalizado, [Crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
3.  En GetServiceCommand.cs, quite el cuerpo del método MenuItemCommand y agregue el código siguiente:  
  
    ```c#  
    IVsActivityLog activityLog = ServiceProvider.GetService(typeof(SVsActivityLog)) as IVsActivityLog; if (activityLog == null) return; System.Windows.Forms.MessageBox.Show("Found the activity log service.");  
  
    ```  
  
     Este código obtiene un servicio SVsActivityLog y lo convierte a un <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interfaz, que puede utilizarse para escribir en el registro de actividad. Para obtener un ejemplo, consulta [Cómo: utilizar el registro de actividad](../extensibility/how-to-use-the-activity-log.md).  
  
4.  Compile la solución y comience la depuración. Aparece la instancia experimental.  
  
5.  En el menú Herramientas de la instancia experimental, busque la **GetServiceCommand invocar** botón. Al hacer clic en este botón, verá un cuadro de mensaje que dice **encuentra el servicio de registro de actividad.**  
  
## Obtención de un servicio de un contenedor de control o ventana de herramienta  
 A veces necesitará obtener un servicio desde una ventana de herramientas o control contenedor que no se ha ubicado, o bien se ha ubicado en un proveedor de servicio que no conozca el servicio que desee. Por ejemplo, puede escribir en el registro de actividad desde dentro de un control.  
  
 Estático <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> método se basa en un proveedor de servicio almacenado en caché que se inicializa la primera vez que se deriva de cualquier VSPackage <xref:Microsoft.VisualStudio.Shell.Package> está ubicado.  
  
 Dado que se llama al constructor de VSPackage antes de que se basa en un VSPackage, servicios globales son normalmente no está disponibles desde dentro del constructor de VSPackage. Consulte [Cómo: solucionar problemas de servicios](../extensibility/how-to-troubleshoot-services.md) para encontrar una solución.  
  
 Este es un ejemplo de la forma de obtener un servicio en una ventana de herramientas o en otro elemento no VSPackage.  
  
```c#  
IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog; if (log == null) return;  
```  
  
## Obtención de un servicio desde el objeto DTE  
 También puede obtener servicios de <xref:EnvDTE.DTEClass> objeto. Sin embargo, debe obtener el objeto DTE como un servicio de un VSPackage o llamando a estático <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> método.  
  
 El objeto DTE implementa <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>, que puede utilizar para consultar un servicio mediante <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A>.  
  
 Aquí se muestra cómo obtener un servicio desde el objeto DTE.  
  
```c#  
// Start with the DTE object, for example: // using EnvDTE; // DTE dte = (DTE)GetService(typeof(DTE)); ServiceProvider sp = new ServiceProvider((Microsoft.VisualStudio.OLE.Interop.IServiceProvider)dte); if (sp != null) { IVsActivityLog log = sp.GetService(typeof(SVsActivityLog)) as IVsActivityLog; if (log != null) { System.Windows.Forms.MessageBox.Show("Found the activity log service."); } }  
```  
  
## Vea también  
 [Cómo: proporcionar un servicio](../extensibility/how-to-provide-a-service.md)   
 [Utilizar y proporcionar servicios](../extensibility/using-and-providing-services.md)   
 [Fundamentos del servicio](../extensibility/internals/service-essentials.md)