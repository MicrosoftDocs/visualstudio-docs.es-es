---
title: Cargando VSPackages | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, loading
ms.assetid: f4c3dcea-5051-4065-898f-601269649d92
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e20caff476e116ad59430692719bdbbe22c4914c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842703"
---
# <a name="loading-vspackages"></a>Carga de VSPackages
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los VSPackages se cargan en Visual Studio solo cuando se requiere su funcionalidad. Por ejemplo, un VSPackage se carga cuando Visual Studio usa un generador de proyectos o un servicio que implementa el VSPackage. Esta característica se denomina carga retrasada, que se usa siempre que sea posible para mejorar el rendimiento.  
  
> [!NOTE]
> Visual Studio puede determinar determinada información de VSPackage, como los comandos que ofrece un VSPackage, sin cargar el VSPackage.  
  
 Los VSPackages se pueden configurar para que se carguen en un contexto de interfaz de usuario determinado, por ejemplo, cuando se abre una solución. El <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> atributo establece este contexto.  
  
### <a name="autoloading-a-vspackage-in-a-specific-context"></a>Cargar autocarga de un VSPackage en un contexto específico  
  
- Agregue el `ProvideAutoLoad` atributo a los atributos de VSPackage:  
  
    ```csharp  
    [DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\14.0")]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid("00000000-0000-0000-0000-000000000000")] // your specific package GUID  
    public class MyAutoloadedPackage : Package  
    {. . .}  
    ```  
  
     Vea los campos enumerados de <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> para obtener una lista de los contextos de la interfaz de usuario y sus valores GUID.  
  
- Establezca un punto de interrupción en el <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> método.  
  
- Compile el VSPackage e inicie la depuración.  
  
- Cargue una solución o cree una.  
  
     El VSPackage se carga y se detiene en el punto de interrupción.  
  
## <a name="forcing-a-vspackage-to-load"></a>Forzar la carga de un VSPackage  
 En algunas circunstancias, es posible que un VSPackage tenga que forzar la carga de otro VSPackage. Por ejemplo, un VSPackage ligero podría cargar un VSPackage mayor en un contexto que no está disponible como CMDUIContext.  
  
 Puede usar el <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A> método para forzar la carga de un VSPackage.  
  
- Inserte este código en el <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> método del VSPackage que fuerza la carga de otro VSPackage:  
  
    ```csharp  
    IVsShell shell = GetService(typeof(SVsShell)) as IVsShell;  
    if (shell == null) return;  
  
    IVsPackage package = null;  
    Guid PackageToBeLoadedGuid =   
        new Guid(Microsoft.PackageToBeLoaded.GuidList.guidPackageToBeLoadedPkgString);  
    shell.LoadPackage(ref PackageToBeLoadedGuid, out package);  
  
    ```  
  
     Cuando se inicializa el VSPackage, se forzará la `PackageToBeLoaded` carga.  
  
     La carga forzada no debe usarse para la comunicación de VSPackage. Use [y proporcione servicios](../extensibility/using-and-providing-services.md) en su lugar.  
  
## <a name="using-a-custom-attribute-to-register-a-vspackage"></a>Usar un atributo personalizado para registrar un VSPackage  
 En algunos casos, puede que tenga que crear un nuevo atributo de registro para la extensión. Puede utilizar atributos de registro para agregar nuevas claves del registro o para agregar nuevos valores a las claves existentes. El nuevo atributo debe derivar de <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> y debe reemplazar los <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> métodos y <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> .  
  
## <a name="creating-a-registry-key"></a>Crear una clave del registro  
 En el código siguiente, el atributo personalizado crea una subclave **personalizada** en la clave para el VSPackage que se está registrando.  
  
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
 Puede agregar valores personalizados a una clave existente. En el código siguiente se muestra cómo agregar un nuevo valor a una clave de registro de VSPackage.  
  
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
  
## <a name="see-also"></a>Consulte también  
 [VSPackages](../extensibility/internals/vspackages.md)
