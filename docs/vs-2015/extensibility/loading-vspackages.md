---
title: Carga de VSPackages | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, loading
ms.assetid: f4c3dcea-5051-4065-898f-601269649d92
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e351f49ea3e9579202e21868361e5d6f3d53b8fd
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51753881"
---
# <a name="loading-vspackages"></a>Carga de VSPackages
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los paquetes VSPackage se cargan en Visual Studio solo cuando su funcionalidad es necesaria. Por ejemplo, un VSPackage se carga cuando Visual Studio utiliza un generador de proyectos o un servicio que implementa el VSPackage. Esta característica se denomina la carga diferida, que se usa siempre que sea posible mejorar el rendimiento.  
  
> [!NOTE]
>  Visual Studio puede determinar cierta información de VSPackage, como los comandos que ofrece un paquete VSPackage, sin tener que cargar el VSPackage.  
  
 VSPackages puede establecerse para cargar automáticamente en un contexto de interfaz (IU) de usuario determinado, por ejemplo, cuando se abre una solución. El <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> atributo establece este contexto.  
  
### <a name="autoloading-a-vspackage-in-a-specific-context"></a>Un VSPackage en un contexto específico de carga automática  
  
-   Agregar el `ProvideAutoLoad` atributo a los atributos de VSPackage:  
  
    ```csharp  
    [DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\14.0")]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid("00000000-0000-0000-0000-000000000000")] // your specific package GUID  
    public class MyAutoloadedPackage : Package  
    {. . .}  
    ```  
  
     Ver los campos enumerados de <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> para obtener una lista de los contextos de interfaz de usuario y sus valores GUID.  
  
-   Establecer un punto de interrupción en el <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> método.  
  
-   Crear el VSPackage e iniciar la depuración.  
  
-   Cargue una solución o cree uno.  
  
     El VSPackage carga y se detiene en el punto de interrupción.  
  
## <a name="forcing-a-vspackage-to-load"></a>Forzar un VSPackage para cargar  
 En algunas circunstancias puede tener un VSPackage forzar que se puede cargar otro paquete VSPackage. Por ejemplo, un VSPackage ligero podría cargar un VSPackage en un contexto que no está disponible como un CMDUIContext más grande.  
  
 Puede usar el <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A> método para forzar la carga de un paquete VSPackage.  
  
-   Inserte este código en el <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> método del VSPackage que obliga a otro VSPackage para cargar:  
  
    ```csharp  
    IVsShell shell = GetService(typeof(SVsShell)) as IVsShell;  
    if (shell == null) return;  
  
    IVsPackage package = null;  
    Guid PackageToBeLoadedGuid =   
        new Guid(Microsoft.PackageToBeLoaded.GuidList.guidPackageToBeLoadedPkgString);  
    shell.LoadPackage(ref PackageToBeLoadedGuid, out package);  
  
    ```  
  
     Cuando se inicializa el VSPackage, forzará `PackageToBeLoaded` para cargar.  
  
     Carga de fuerza no debe usarse para la comunicación de VSPackage. Use [Using y proporcionar servicios](../extensibility/using-and-providing-services.md) en su lugar.  
  
## <a name="using-a-custom-attribute-to-register-a-vspackage"></a>Uso de un atributo personalizado para registrar un VSPackage  
 En algunos casos es posible que deberá crear un nuevo atributo de registro para la extensión. Puede usar los atributos de registro para agregar nuevas claves del registro o para agregar nuevos valores a las claves existentes. El nuevo atributo debe derivar de <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>, y debe invalidar el <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> y <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> métodos.  
  
## <a name="creating-a-registry-key"></a>Creación de una clave del registro  
 En el código siguiente, se crea el atributo personalizado un **personalizado** subclave bajo la clave para el VSPackage que se va a registrar.  
  
```csharp  
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
  
## <a name="creating-a-new-value-under-an-existing-registry-key"></a>Crear un nuevo valor en una clave del registro existente  
 Puede agregar valores personalizados para una clave existente. El código siguiente muestra cómo agregar un nuevo valor a una clave de registro de VSPackage.  
  
```csharp  
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
  
## <a name="see-also"></a>Vea también  
 [VSPackages](../extensibility/internals/vspackages.md)

