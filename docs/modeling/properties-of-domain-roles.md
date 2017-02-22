---
title: "Propiedades de los roles de dominio | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5a7bb18c-638e-45e8-9d79-9aa6a9e14b0e
caps.latest.revision: 9
caps.handback.revision: 9
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Propiedades de los roles de dominio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Las propiedades en la tabla siguiente son asociado a un rol del dominio.  Para obtener información sobre los roles de dominio, vea [Introducción a los modelos, las clases y las relaciones](../modeling/understanding-models-classes-and-relationships.md).  Para obtener más información sobre cómo utilizar estas propiedades, vea [Personalizar y ampliar lenguajes específicos de dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
|Propiedad.|Descripción|Default|  
|----------------|-----------------|-------------|  
|Tipo de coleccin|si este rol tiene multiplicidad de 0. \* o 1.\*, esta propiedad personaliza el tipo genérico que se utiliza para almacenar la colección de vínculos.|`(none)`se utiliza \- <xref:Microsoft.VisualStudio.Modeling.LinkedElementCollection%601>|  
|Atributos personalizados|Los atributos que se especifiquen aquí se agregarán como atributos a la clase generada del código.|\<none\>|  
|Es la propiedad modificable|Si `True`y, si la multiplicidad de la relación es 0..1 o 1..1, esta propiedad se puede explorar por el usuario en la ventana de **Propiedades** .  La propiedad muestra el nombre del elemento en el otro extremo del vínculo de la relación.|`True`|  
|es el generador de la propiedad|Si `True`, un rol de propiedad se genera para este rol, que puede utilizar para recorrer la relación en código de programa.  Si establece este false, puede recorrer la relación de una manera menos eficaz mediante los métodos estáticos de la relación de dominio.|`True`|  
|Modificador de acceso get de la propiedad|El modificador de acceso del captador para la propiedad generada \(`public`, `internal`, `private`, `protected`, o `protected internal`\).|`public`|  
|Modificador de acceso set de la propiedad|El modificador de acceso del establecedor de la propiedad generada \(`public`, `internal`, `private`, `protected`, o `protected internal`\).|`public`|  
|Multiplicity|El número de elementos de modelo que desempeñan el rol contrario \(`0..1`, `1..1`, `0..*`, o `1..*`\).  Si la multiplicidad es `0..*` o `1..*`, la propiedad generada representa una colección; si no, la propiedad generada representa un solo elemento de modelo.|Depende del tipo de relación y si es el rol de origen o de destino en la relación.|  
|Name|El nombre del rol del dominio.  Esta propiedad no puede contener espacios en blanco.|El nombre de la clase de dominio del encargado de función para este rol.|  
|Propaga la copia|`DoNotPropagateCopy` \- el encargado de función copiado no tendrá ninguna copia de este vínculo.<br /><br /> `PropagateCopyToLinkOnly` \- The copió los puntos del vínculo al existente opuesta de encargado de función.<br /><br /> `PropagateCopyToLinkAndOppositeRolePlayer`\- puntos copiados el vínculo a una copia del encargado de rol opuesto.|`PropagateCopyToLinkAndOppositeRolePlayer` para los roles del origen de embeddings.<br /><br /> `DoNotPropagateCopy` de otros roles.<br /><br /> Para obtener más información, vea [Personalizar comportamiento de copia](../modeling/customizing-copy-behavior.md).|  
|Propaga Suprimir|`True` para eliminar el elemento que realiza este rol cuando se elimine el vínculo asociado.|`True` para el destino de un rol de incrustación.<br /><br /> `False` de otros roles.<br /><br /> Para obtener más información, vea [Personalizar el comportamiento de eliminación](../modeling/customizing-deletion-behavior.md).|  
|Nombre de la propiedad|El nombre de la propiedad generada en el código del encargado de función.  Este nombre no puede contener espacios en blanco.|El nombre del rol contrario si este rol tiene a cero\-a\-uno o una multiplicidad una por; si no, el nombre pluralized de rol opuesto.|  
|encargado de función|La clase de dominio del elemento que puede desempeñar este rol en la relación.  Esta propiedad es de sólo lectura.|La clase de dominio de encargado de función para este rol.|  
|Notas|Notas informales que son asociado al rol del dominio.|\<none\>|  
|Categoría|La categoría en la que la propiedad generada aparece en la ventana de **Propiedades** en el diseñador generado.  Si esta propiedad está vacía, la propiedad generada aparece bajo la categoría de **Varias**|\<none\>|  
|Descripción|La descripción que se utiliza al código del documento y se utiliza en la interfaz de usuario del diseñador generado.<br /><br /> La descripción aparece en la información sobre herramientas de Intellisense para la propiedad generada en la clase de encargado de función.|`Description for` *el nombre completo del rol*|  
|Nombre para mostrar|El nombre que se muestra en el diseñador generado para el rol del dominio.|el valor ajustado de la propiedad Name.|  
|Palabra clave de Ayuda|La palabra clave opcional que se utiliza para la ayuda de F1 de índice para el rol del dominio.|\<none\>|  
|nombre para mostrar de la propiedad|El nombre que se muestra en el diseñador generado para el rol generado de la propiedad.|El valor ajustado de la propiedad de nombre de propiedad.|  
  
> [!NOTE]
>  El valor predeterminado de un nombre para mostrar es según el valor de propiedad asociado insertar espacios delante de cada carácter una mayúscula que es precedido por un carácter en minúscula y que no sea seguido por otro carácter una mayúscula.  
  
## Vea también  
 [Propiedades de las relaciones de dominio](../modeling/properties-of-domain-relationships.md)