---
title: Registro y anulación del registro de vsPackages | Microsoft Docs
description: Obtenga información sobre cómo registrar y anular el registro de los VSPackages, incluidos los atributos que usa y el archivo .pkgdef.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: e25e7a46-6a55-4726-8def-ca316f553d6b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 48067ed883a44870b3b753cb5e3d6943eca91ca5
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900309"
---
# <a name="register-and-unregister-vspackages"></a>Registro y anulación del registro de VSPackages
Los atributos se usan para registrar un VSPackage, pero

## <a name="register-a-vspackage"></a>Registrar un VSPackage
 Puede usar atributos para controlar el registro de VSPackages administrados. Toda la información de registro está contenida en un *archivo .pkgdef.* Para obtener más información sobre el registro basado en archivos, vea [La utilidad CreatePkgDef](../extensibility/internals/createpkgdef-utility.md).

 El código siguiente muestra cómo usar los atributos de registro estándar para registrar el VSPackage.

```csharp
[PackageRegistration(UseManagedResourcesOnly = true)]
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]
public sealed class BasicPackage : Package
{
    // ...
}
```

## <a name="unregister-an-extension"></a>Cancelar el registro de una extensión
 Si ha estado experimentando con una gran cantidad de VSPackages diferentes y desea quitarlos de la instancia experimental, solo tiene que ejecutar el **comando Restablecer.** Busque **Restablecer la Visual Studio experimental en** la página de inicio del equipo o ejecute este comando desde la línea de comandos:

```cmd
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp
```

 Si desea desinstalar una extensión que ha instalado en la instancia de desarrollo de Visual Studio, vaya a Herramientas extensiones y actualizaciones, busque la extensión y haga clic en  >   **Desinstalar**.

 Si, por alguna razón, ninguno de estos métodos desinstala correctamente la extensión, puede anular el registro del ensamblado VSPackage de la línea de comandos como se muestra a continuación:

```cmd
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg" /unregister <pathToVSPackage assembly>
```

<a name="using-a-custom-registration-attribute-to-register-an-extension"></a>

## <a name="use-a-custom-registration-attribute-to-register-an-extension"></a>Uso de un atributo de registro personalizado para registrar una extensión

En algunos casos, es posible que tenga que crear un nuevo atributo de registro para la extensión. Puede usar atributos de registro para agregar nuevas claves del Registro o para agregar nuevos valores a las claves existentes. El nuevo atributo debe derivar de <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> y debe invalidar los <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> métodos y .

### <a name="create-a-custom-attribute"></a>Creación de un atributo personalizado

El código siguiente muestra cómo crear un nuevo atributo de registro.

```csharp
[AttributeUsage(AttributeTargets.Class, Inherited = true, AllowMultiple = false)]
public class CustomRegistrationAttribute : RegistrationAttribute
{
}
```

 se usa en las clases de atributo para especificar el elemento de programa (clase, método, etc.) al que pertenece el atributo, si se puede usar más de una vez y si se puede <xref:System.AttributeUsageAttribute> heredar.

### <a name="create-a-registry-key"></a>Creación de una clave del Registro

En el código siguiente, el atributo personalizado crea una subclave **Custom** bajo la clave para el VSPackage que se está registrando.

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

### <a name="create-a-new-value-under-an-existing-registry-key"></a>Creación de un nuevo valor en una clave del Registro existente

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

## <a name="see-also"></a>Consulta también
- [VSPackages](../extensibility/internals/vspackages.md)
