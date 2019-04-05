---
title: Uso de un atributo de registro personalizado para registrar una extensión | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: 98068fa7-bda1-4922-b3f6-28680de58c3d
caps.latest.revision: 3
manager: jillfra
ms.openlocfilehash: a619c5d418df3b9b85ab09cf9b907617ebd81b67
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58995606"
---
# <a name="using-a-custom-registration-attribute-to-register-an-extension"></a>Usar un atributo de registro personalizado para registrar una extensión
En algunos casos es posible que deberá crear un nuevo atributo de registro para la extensión. Puede usar los atributos de registro para agregar nuevas claves del registro o para agregar nuevos valores a las claves existentes. El nuevo atributo debe derivar de <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>, y debe invalidar el <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> y <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> métodos.  
  
## <a name="creating-a-custom-attribute"></a>Crear un atributo personalizado  
 El código siguiente muestra cómo crear un nuevo atributo de registro.  
  
```  
[AttributeUsage(AttributeTargets.Class, Inherited = true, AllowMultiple = false)]  
    public class CustomRegistrationAttribute : RegistrationAttribute  
    {  
    }  
  
```  
  
 El <xref:System.AttributeUsageAttribute> se usa en clases de atributos para especificar el elemento de programa (clase, método, etc.) al que pertenece el atributo, si se puede usar más de una vez y si puede heredarse.  
  
### <a name="creating-a-registry-key"></a>Creación de una clave del registro  
 En el código siguiente, se crea el atributo personalizado un **personalizado** subclave bajo la clave para el VSPackage que se va a registrar.  
  
```  
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
 Puede agregar valores personalizados para una clave existente. El código siguiente muestra cómo agregar un nuevo valor a una clave de registro de VSPackage.  
  
```  
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