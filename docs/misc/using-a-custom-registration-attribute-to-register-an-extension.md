---
title: "Usar un atributo de registro personalizado para registrar una extensi&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 98068fa7-bda1-4922-b3f6-28680de58c3d
caps.latest.revision: 3
caps.handback.revision: 3
manager: "douge"
---
# Usar un atributo de registro personalizado para registrar una extensi&#243;n
En algunos casos puede ser necesario crear un atributo del nuevo registro para la extensión.  Puede usar los atributos del registro para agregar las nuevas claves del Registro o agregar nuevos valores a las claves existentes.  El nuevo atributo debe derivar de <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>, y debe invalidar el <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> y los métodos de <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> .  
  
## crear un atributo personalizado  
 El código siguiente muestra cómo crear un atributo del nuevo registro.  
  
```  
[AttributeUsage(AttributeTargets.Class, Inherited = true, AllowMultiple = false)]  
    public class CustomRegistrationAttribute : RegistrationAttribute  
    {  
    }  
  
```  
  
 <xref:System.AttributeUsageAttribute> se utiliza en clases de atributos para especificar el elemento de programa \(clase, método, etc.\). al que el atributo pertenece, si puede utilizar más de una vez, y si se puede heredar.  
  
### Crear una clave del Registro  
 En el código siguiente, el atributo personalizado crea una subclave personalizada de clave para el Paquete se está registrando que.  
  
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
  
### Crear un valor En New una clave del Registro Existente  
 Puede agregar valores personalizados a una clave existente.  El código siguiente muestra cómo agregar un nuevo valor en una clave del registro de VSPackage.  
  
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