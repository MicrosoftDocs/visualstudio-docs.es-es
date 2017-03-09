---
title: "La versi&#243;n de dise&#241;o personalizado de &#39;System.Runtime.CompilerServices.ExtensionAttribute&#39; que encontr&#243; el compilador no es v&#225;lida | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc36558"
  - "bc36558"
helpviewer_keywords: 
  - "BC36558"
ms.assetid: f47d310a-95fd-4340-bda2-21262c217dbb
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La versi&#243;n de dise&#241;o personalizado de &#39;System.Runtime.CompilerServices.ExtensionAttribute&#39; que encontr&#243; el compilador no es v&#225;lida
La versión de diseño personalizado de 'System.Runtime.CompilerServices.ExtensionAttribute' que encontró el compilador no es válida. Sus marcas de uso de atributos deben establecerse para permitir ensamblados, clases y métodos.  
  
 La versión de diseño personalizado de <xref:System.Runtime.CompilerServices.ExtensionAttribute?displayProperty=fullName> que el compilador encontró no establece las marcas de uso de atributos para permitir la aplicación del atributo a ensamblados, métodos y clases. Se requiere la aplicación para al menos los tres elementos de programa.  
  
 **Identificador de error:** BC36558  
  
### Para corregir este error  
  
-   Cambie la definición de atributo para permitir que el atributo se aplique como mínimo a ensamblados, métodos y clases, tal como se muestra en los ejemplos siguientes.  
  
-   Use <xref:System.Runtime.CompilerServices.ExtensionAttribute?displayProperty=fullName> en lugar de la versión de diseño personalizado.  
  
## Ejemplo  
 En el ejemplo siguiente se usa el atributo `AttributeUsage` para especificar a qué elementos del programa se puede aplicar la nueva versión de `ExtensionAttribute`. En el ejemplo se especifican tres miembros de la enumeración `AttributeTargets`: `Assembly`, `Class` y `Method`. La omisión de cualquiera de estos elementos provocará este error.  
  
```  
Namespace System.Runtime.CompilerServices <AttributeUsage(AttributeTargets.Assembly Or _ AttributeTargets.Class Or AttributeTargets.Method)> Class ExtensionAttribute Inherits System.Attribute ' Definitions of methods, fields, and properties. End Class End Namespace  
```  
  
 Como alternativa, puede permitir que `ExtensionAttribute` se aplique a todos los elementos del programa mediante el miembro `All` de `AttributeTargets`.  
  
```  
<AttributeUsage(AttributeTargets.All)>  
```  
  
 Al eliminar la línea `AttributeUsage`, como se muestra en el código siguiente, se produce el mismo resultado.  
  
```  
Namespace System.Runtime.CompilerServices Class ExtensionAttribute Inherits System.Attribute ' Definitions of methods, fields, and properties. End Class End Namespace  
```  
  
## Vea también  
 <xref:System.Runtime.CompilerServices.ExtensionAttribute>   
 [NO ESTÁ EN LA COMPILACIÓN: Información general de atributos en Visual Basic](http://msdn.microsoft.com/es-es/0d0cff64-892d-4f57-83bd-bef388553d4f)   
 [NO ESTÁ EN LA COMPILACIÓN: Atributos personalizados en Visual Basic](http://msdn.microsoft.com/es-es/d72d8a5c-8f64-4614-b15b-cad66845d047)   
 [métodos de extensión.](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [NO ESTÁ EN LA COMPILACIÓN: Cómo: Definir atributos propios](http://msdn.microsoft.com/es-es/039609c4-ec43-4f44-945f-aa3b5b535c6a)   
 [Escribir atributos personalizados](../Topic/Writing%20Custom%20Attributes.md)