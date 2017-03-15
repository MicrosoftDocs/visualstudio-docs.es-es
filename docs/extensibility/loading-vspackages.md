---
title: "Cargar VSPackages | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSPackages, carga automática"
  - "VSPackages, cargar"
ms.assetid: f4c3dcea-5051-4065-898f-601269649d92
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# Cargar VSPackages
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VSPackages solo se cargan en Visual Studio cuando se requiere su función. Por ejemplo, un paquete VSPackage se cargará cuando Visual Studio utiliza un generador del proyecto o un servicio que implementa el VSPackage. Esta característica se llama carga diferida, que se utiliza siempre que sea posible mejorar el rendimiento.  
  
> [!NOTE]
>  Visual Studio puede determinar cierta información de VSPackage, como los comandos que ofrece un paquete VSPackage, sin necesidad de cargar el VSPackage.  
  
 VSPackages puede establecerse para cargar automáticamente en un contexto de usuario determinado \(interfaz\), por ejemplo, cuando se abre una solución. El <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> atributo establece este contexto.  
  
### Carga automática un VSPackage en un contexto específico  
  
-   Agregue el `ProvideAutoLoad` de atributo para los atributos de VSPackage:  
  
    ```c#  
    [DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\14.0")]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid("00000000-0000-0000-0000-000000000000")] // your specific package GUID  
    public class MyAutoloadedPackage : Package  
    {. . .}  
    ```  
  
     Consulte los campos enumerados de <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> para obtener una lista de los contextos de la interfaz de usuario y sus valores GUID.  
  
-   Establecer un punto de interrupción en la <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> \(método\).  
  
-   Compilar el VSPackage e iniciar la depuración.  
  
-   Cargar una solución o crear uno.  
  
     El VSPackage se carga y se detiene en el punto de interrupción.  
  
## Forzar un VSPackage cargar  
 En algunas circunstancias puede tener un VSPackage forzar que otro paquete VSPackage que se va a cargar. Por ejemplo, un VSPackage ligero podría cargar un paquete VSPackage mayor en un contexto que no está disponible como un CMDUIContext.  
  
 Puede usar el <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A> método para forzar un VSPackage para cargar.  
  
-   Inserte el código siguiente en el <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> método de VSPackage que impone el VSPackage otra para cargar:  
  
    ```c#  
    IVsShell shell = GetService(typeof(SVsShell)) as IVsShell;  
    if (shell == null) return;  
  
    IVsPackage package = null;  
    Guid PackageToBeLoadedGuid =   
        new Guid(Microsoft.PackageToBeLoaded.GuidList.guidPackageToBeLoadedPkgString);  
    shell.LoadPackage(ref PackageToBeLoadedGuid, out package);  
  
    ```  
  
     Cuando se inicializa el VSPackage, forzará `PackageToBeLoaded` para cargar.  
  
     Carga de fuerza no debe utilizarse para la comunicación de VSPackage. Utilice [Utilizar y proporcionar servicios](../extensibility/using-and-providing-services.md) en su lugar.  
  
## Uso de un atributo personalizado para registrar un paquete VSPackage  
 En ciertos casos, debe crear un nuevo atributo de registro para la extensión. Puede usar atributos de registro para agregar nuevas claves del registro o para agregar nuevos valores a las claves existentes. El nuevo atributo debe derivar de <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>, y se debe reemplazar el <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> y <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> métodos.  
  
## Crear una clave del registro  
 En el siguiente código, el atributo personalizado crea un **personalizado** subclave bajo la clave para el paquete VSPackage que se va a registrar.  
  
```c#  
public override void Register(RegistrationAttribute.RegistrationContext context)  
{  
    Key packageKey = null;  
    try  
    {   
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + @"}\Custom");  
        packageKey.SetValue("NewCustom", 1);  
    }  
    finally  
    {  
        if (packageKey != null)  
            packageKey.Close();  
    }  
}  
  
public override void Unregister(RegistrationContext context)  
{  
    context.RemoveKey(@"Packages\" + context.ComponentType.GUID + @"}\Custom");  
}  
  
```  
  
## Crear un nuevo valor en una clave del registro existente  
 Puede agregar valores personalizados a una clave existente. El código siguiente muestra cómo agregar un nuevo valor a una clave de registro de VSPackage.  
  
```c#  
public override void Register(RegistrationAttribute.RegistrationContext context)  
{  
    Key packageKey = null;  
    try  
    {   
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + "}");  
        packageKey.SetValue("NewCustom", 1);  
    }  
    finally  
    {  
        if (packageKey != null)  
            packageKey.Close();  
                }  
}  
  
public override void Unregister(RegistrationContext context)  
{  
    context.RemoveValue(@"Packages\" + context.ComponentType.GUID, "NewCustom");  
}  
```  
  
## Vea también  
 [VSPackages](../extensibility/internals/vspackages.md)