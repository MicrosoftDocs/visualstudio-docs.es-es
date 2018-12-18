---
title: Registrar y anular el registro de VSPackages | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: e25e7a46-6a55-4726-8def-ca316f553d6b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2075bec37e29359fb9c403f9cb149b70c01845b6
ms.sourcegitcommit: 9571742f4a808c75b1034aa72fc24b54bc50692e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2018
ms.locfileid: "49410993"
---
# <a name="register-and-unregister-vspackages"></a>Registrar y anular el registro de VSPackages
Usar atributos para registrar un VSPackage, pero  
  
## <a name="register-a-vspackage"></a>Registrar un VSPackage  
 Puede usar atributos para controlar el registro de VSPackages administrados. Toda la información de registro se encuentra en un *.pkgdef* archivo. Para obtener más información sobre el registro de archivo, consulte [utilidad CreatePkgDef](../extensibility/internals/createpkgdef-utility.md).  
  
 El código siguiente muestra cómo utilizar los atributos de registro estándar para registrar el VSPackage.  
  
```csharp  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]  
public sealed class BasicPackage : Package  
{
    // ...
}  
```  
  
## <a name="unregister-an-extension"></a>Anular el registro de una extensión  
 Si ha estado experimentando con una gran cantidad de VSPackages diferentes y eliminarlos de la instancia experimental, puede ejecutar simplemente el **restablecer** comando. Busque **restablecer la instancia Experimental de Visual Studio** en la página de inicio del equipo, o ejecute este comando desde la línea de comandos:  
  
```cmd  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp  
```  
  
 Si desea desinstalar una extensión que ha instalado en su instancia de desarrollo de Visual Studio, vaya a **herramientas** > **extensiones y actualizaciones**, busque la extensión y haga clic en  **Desinstalar**.  
  
 Si por algún motivo, ninguno de estos métodos es correcta al desinstalar la extensión, puede anular el registro del ensamblado de VSPackage desde la línea de comandos como sigue:  
  
```cmd  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg" /unregister <pathToVSPackage assembly>  
```  
  
<a name="using-a-custom-registration-attribute-to-register-an-extension"></a>  
  
## <a name="use-a-custom-registration-attribute-to-register-an-extension"></a>Utilice un atributo de registro personalizado para registrar una extensión  
  
En algunos casos es posible que deberá crear un nuevo atributo de registro para la extensión. Puede usar los atributos de registro para agregar nuevas claves del registro o para agregar nuevos valores a las claves existentes. El nuevo atributo debe derivar de <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>, y debe invalidar el <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> y <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> métodos.  
  
### <a name="create-a-custom-attribute"></a>Crear un atributo personalizado  
  
El código siguiente muestra cómo crear un nuevo atributo de registro.  
  
```csharp  
[AttributeUsage(AttributeTargets.Class, Inherited = true, AllowMultiple = false)]  
public class CustomRegistrationAttribute : RegistrationAttribute  
{  
}  
```  
  
 El <xref:System.AttributeUsageAttribute> se usa en clases de atributos para especificar el elemento de programa (clase, método, etc.) al que pertenece el atributo, si se puede usar más de una vez y si puede heredarse.  
  
### <a name="create-a-registry-key"></a>Crear una clave del registro  
  
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
  
### <a name="create-a-new-value-under-an-existing-registry-key"></a>Cree un nuevo valor en una clave del registro existente  
  
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
