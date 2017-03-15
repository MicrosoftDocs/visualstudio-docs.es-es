---
title: "Propiedades de las clases de dominio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Lenguaje específico de dominio, clase de dominio"
ms.assetid: a3993995-19e7-4761-a972-b1de89131a1b
caps.latest.revision: 21
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 21
---
# Propiedades de las clases de dominio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Las clases de dominio tienen las propiedades en la tabla siguiente.  Para obtener información sobre clases de dominio, vea [Introducción a los modelos, las clases y las relaciones](../modeling/understanding-models-classes-and-relationships.md).  Para obtener más información sobre cómo utilizar estas propiedades, vea [Personalizar y ampliar lenguajes específicos de dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
|Propiedad.|Descripción|Default|  
|----------------|-----------------|-------------|  
|Modificador de acceso|El nivel de acceso de la clase de dominio \(`public` o `internal`\).|`public`|  
|Atributos personalizados|Se utiliza para agregar atributos a la clase del código fuente generado con esta clase de dominio.|\<none\>|  
|genera derivado doble|Si `True`, una clase base y una clase parcial \(para admitir la personalización reemplaza a través\) se genera.  Para obtener más información, vea [Invalidar y ampliar clases generadas](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|  
|tiene el constructor personalizado|Si `True`, un constructor personalizado proporcionado en el código fuente.  Para obtener más información, vea [Invalidar y ampliar clases generadas](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|  
|Modificador de herencia|Describe la clase de herencia de clases de código fuente que se genera a partir de la clase de dominio \(`none`, `abstract` o `sealed`\).|`none`|  
|Clase base|Si esta clase de dominio es derivada, el nombre de la clase base.|\<none\>|  
|Name|El nombre de esta clase de dominio.|nombre actual|  
|Espacio de nombres|El espacio de nombres de esta clase de dominio.|espacio de nombres actual|  
|Notas|Notas informales que son asociado a esta clase de dominio.|\<none\>|  
|Descripción|La descripción que se utiliza para documentar la interfaz de usuario del diseñador generado.|\<none\>|  
|Nombre para mostrar|El nombre que se mostrará en el diseñador generado para esta clase de dominio.|\<none\>|  
|Palabra clave de Ayuda|La palabra clave opcional que se utiliza para la ayuda de F1 de índice para esta clase de dominio.|\<none\>|  
  
## Vea también  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/es-es/ca5e84cb-a315-465c-be24-76aa3df276aa)