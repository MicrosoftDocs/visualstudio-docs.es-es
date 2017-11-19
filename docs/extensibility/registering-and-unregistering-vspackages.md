---
title: Registrar y anular el registro de VSPackages | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: e25e7a46-6a55-4726-8def-ca316f553d6b
caps.latest.revision: "35"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4443195babbe3f8926633a992aa942dcb80dc3f3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="registering-and-unregistering-vspackages"></a>Registrar y anular el registro de VSPackages
Usar atributos para registrar un paquete VSPackage, pero  
  
## <a name="registering-a-vspackage"></a>Registrar un VSPackage  
 Puede usar atributos para controlar el registro de VSPackages administrado. Toda la información de registro se encuentra en un archivo .pkgdef. Para obtener más información sobre basados en archivos de registro, consulte [CreatePkgDef utilidad](../extensibility/internals/createpkgdef-utility.md).  
  
 El código siguiente muestra cómo usar los atributos de registro estándar para registrar el VSPackage.  
  
```csharp  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]  
public sealed class BasicPackage : Package  
{. . .}  
```  
  
## <a name="unregistering-an-extension"></a>Al anular el registro de una extensión  
 Si ha variado con una gran cantidad de VSPackages diferentes y eliminarlos de la instancia experimental, puede ejecutar simplemente el **restablecer** comando. Busque **restablecer la instancia Experimental de Studio Visual** en la página de inicio del equipo, o ejecutar este comando desde la línea de comandos:  
  
```vb  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp  
```  
  
 Si desea desinstalar una extensión que instaló en su instancia de desarrollo de Visual Studio, vaya a **herramientas / extensiones y actualizaciones**, busque la extensión y haga clic en **desinstalar**.  
  
 Si por algún motivo, ninguno de estos métodos es correcta al desinstalar la extensión, puede anular el registro del ensamblado de VSPackage desde la línea de comandos como se indica a continuación:  
  
```  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg" /unregister <pathToVSPackage assembly>  
```  
  
<a name="using-a-custom-registration-attribute-to-register-an-extension"></a>  
  
## <a name="use-a-custom-registration-attribute-to-register-an-extension"></a>Usar un atributo de registro personalizado para registrar una extensión  
  
En ciertos casos, debe crear un nuevo atributo de registro para la extensión. Puede utilizar atributos de registro para agregar nuevas claves del registro o para agregar nuevos valores a las claves existentes. El nuevo atributo debe derivar de <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>, y debe invalidar el <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> y <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> métodos.  
  
### <a name="creating-a-custom-attribute"></a>Crear un atributo personalizado  
  
El código siguiente muestra cómo crear un nuevo atributo de registro.  
  
```csharp  
[AttributeUsage(AttributeTargets.Class, Inherited = true, AllowMultiple = false)]  
    public class CustomRegistrationAttribute : RegistrationAttribute  
    {  
    }  
```  
  
 El <xref:System.AttributeUsageAttribute> se usa en clases de atributos para especificar el elemento de programa (clase, método, etc.) al que pertenece el atributo, si se puede utilizar más de una vez, y si puede heredarse.  
  
### <a name="creating-a-registry-key"></a>Crear una clave del registro  
  
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
  
### <a name="creating-a-new-value-under-an-existing-registry-key"></a>Crear un nuevo valor en una clave del registro existente  
  
Puede agregar valores personalizados a una clave existente. El código siguiente muestra cómo agregar un nuevo valor a una clave de registro de VSPackage.  
  
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