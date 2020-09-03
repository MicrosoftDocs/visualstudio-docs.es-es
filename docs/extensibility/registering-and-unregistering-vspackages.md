---
title: Registrar y anular el registro de VSPackages | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: e25e7a46-6a55-4726-8def-ca316f553d6b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f345bdbd3cf5858d495937c743b580abf5e3dd50
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80701578"
---
# <a name="register-and-unregister-vspackages"></a>Registrar y anular el registro de VSPackages
Los atributos se usan para registrar un VSPackage, pero

## <a name="register-a-vspackage"></a>Registrar un VSPackage
 Puede usar atributos para controlar el registro de los VSPackages administrados. Toda la información de registro se encuentra en un archivo *. pkgdef* . Para obtener más información sobre el registro basado en archivos, consulte [utilidad CreatePkgDef](../extensibility/internals/createpkgdef-utility.md).

 En el código siguiente se muestra cómo usar los atributos estándar de registro para registrar el VSPackage.

```csharp
[PackageRegistration(UseManagedResourcesOnly = true)]
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]
public sealed class BasicPackage : Package
{
    // ...
}
```

## <a name="unregister-an-extension"></a>Cancelar el registro de una extensión
 Si ha estado experimentando con muchos VSPackages diferentes y desea quitarlos de la instancia experimental, solo puede ejecutar el comando de **restablecimiento** . Busque **restablecer la instancia experimental de Visual Studio** en la página de inicio del equipo o ejecute este comando desde la línea de comandos:

```cmd
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp
```

 Si desea desinstalar una extensión que ha instalado en la instancia de desarrollo de Visual Studio, vaya a **herramientas**  >  **extensiones y actualizaciones**, busque la extensión y haga clic en **desinstalar**.

 Si, por alguna razón, ninguno de estos métodos se ejecuta correctamente en la desinstalación de la extensión, puede anular el registro del ensamblado VSPackage desde la línea de comandos de la siguiente manera:

```cmd
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg" /unregister <pathToVSPackage assembly>
```

<a name="using-a-custom-registration-attribute-to-register-an-extension"></a>

## <a name="use-a-custom-registration-attribute-to-register-an-extension"></a>Usar un atributo de registro personalizado para registrar una extensión

En algunos casos, puede que tenga que crear un nuevo atributo de registro para la extensión. Puede utilizar atributos de registro para agregar nuevas claves del registro o para agregar nuevos valores a las claves existentes. El nuevo atributo debe derivar de <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> y debe reemplazar los <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> métodos y <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> .

### <a name="create-a-custom-attribute"></a>Creación de un atributo personalizado

En el código siguiente se muestra cómo crear un nuevo atributo de registro.

```csharp
[AttributeUsage(AttributeTargets.Class, Inherited = true, AllowMultiple = false)]
public class CustomRegistrationAttribute : RegistrationAttribute
{
}
```

 <xref:System.AttributeUsageAttribute>Se utiliza en las clases de atributos para especificar el elemento de programa (clase, método, etc.) al que pertenece el atributo, si se puede usar más de una vez y si se puede heredar.

### <a name="create-a-registry-key"></a>Crear una clave del registro

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

### <a name="create-a-new-value-under-an-existing-registry-key"></a>Crear un nuevo valor en una clave del registro existente

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

## <a name="see-also"></a>Vea también
- [VSPackages](../extensibility/internals/vspackages.md)
