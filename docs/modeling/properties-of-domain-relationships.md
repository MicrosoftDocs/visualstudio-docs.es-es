---
title: "Propiedades de las relaciones de dominio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Lenguaje específico de dominio, relaciones de dominio"
ms.assetid: 9ccb3dc2-b80c-4585-932f-3c5f87bafbcd
caps.latest.revision: 20
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 20
---
# Propiedades de las relaciones de dominio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Las propiedades en la siguiente tabla están asociadas con una relación de dominio. Para obtener información acerca de las relaciones de dominio, consulte [Descripción de los modelos, las clases y relaciones](../modeling/understanding-models-classes-and-relationships.md). Para obtener más información acerca de cómo utilizar estas propiedades, vea [Personalizar y ampliar un lenguaje específico de dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
|Propiedad|Descripción|Predeterminado|  
|--------------|-----------------|-------------|  
|Modificador de acceso|El nivel de acceso de la relación de dominio (`public` o `internal`).|`public`|  
|Atributos personalizados|Se utiliza para agregar atributos a la clase de código de origen que se genera a partir de la relación de dominio.|\< none>|  
|Genera doble derivadas|Si `True`, se genera una clase base y una clase parcial (para admitir la personalización mediante invalidaciones). Para obtener más información, vea [Reemplazar y ampliar las clases generadas](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|  
|Tiene un Constructor personalizado|Si `True`, indica que se proporciona un constructor personalizado en el código fuente. Para obtener más información, vea [Reemplazar y ampliar las clases generadas](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|  
|Modificador de herencia|Describe el tipo de herencia de la clase de código de origen que se genera a partir de la relación de dominio (`none`, `abstract` o `sealed`).|\< none>|  
|Permite duplicados|Si `True`, se crearán vínculos duplicados de la relación de dominio entre los dos mismos elementos.|`False`|  
|Relaciones de base|Si se deriva la relación de dominio, la relación de base de la relación de dominio.|\< none>|  
|Es incrustar|Si `True`, la relación de dominio es una relación de incrustación. Si `False`, la relación es una relación de referencia.|\< ambos>|  
|Nombre|El nombre de la relación de dominio.|Nombre actual|  
|Espacio de nombres|El espacio de nombres que está afiliado a la relación de dominio.|Espacio de nombres actual|  
|Notas|Notas informales que están asociadas a la relación de dominio.|\< none>|  
|Descripción|La descripción que se usa para documentar código y se usa en la interfaz de Usuario del diseñador generado.|\< none>|  
|Nombre para mostrar|El nombre que se muestra en el diseñador generado para la relación de dominio.|\< none>|  
|Palabra clave de ayuda|La palabra clave opcional que se utiliza para indizar la Ayuda de F1 para la relación de dominio.|\< none>|  
  
## <a name="see-also"></a>Vea también  
 [Glosario de herramientas de lenguaje específico de dominio](http://msdn.microsoft.com/es-es/ca5e84cb-a315-465c-be24-76aa3df276aa)