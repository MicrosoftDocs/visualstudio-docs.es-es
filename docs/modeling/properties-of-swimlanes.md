---
title: "Propiedades de las calles | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.dsltools.dsldesigner.swimlane"
helpviewer_keywords: 
  - "Lenguaje específico de dominio, calle"
ms.assetid: 47edbc2d-09e4-48ac-b4d1-5268a06a27e6
caps.latest.revision: 24
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 24
---
# Propiedades de las calles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede agregar calles a un diagrama.  División de Calles un diagrama en áreas vertical u horizontal.  Puede definir otras formas que se mostrarán en calles.  Para obtener más información, vea [Cómo: Definir lenguajes específicos de dominio](../modeling/how-to-define-a-domain-specific-language.md).  Para obtener más información sobre cómo utilizar estas propiedades, vea [Personalizar y ampliar lenguajes específicos de dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 Calles tiene propiedades que se muestran en la tabla siguiente.  
  
|Propiedad.|Descripción|Default|  
|----------------|-----------------|-------------|  
|Color de relleno de cuerpo|El color de relleno para el cuerpo de calle.|Blanco|  
|Color de relleno de encabezado|El color de relleno para el encabezado de calle.|gris oscuro|  
|separador Color|El color de la línea de separador.|gris claro|  
|Estilo de línea separadora|El estilo de la línea de separador \(`Solid`, `Dash`, `Dot`, `DashDot`, `DashDotDot`, o `Custom`\).|`Dash`|  
|Grosor de separador|El grosor de línea separadora en pulgadas.|0.03125|  
|Color del texto|El color que se utiliza para los elementos decorator de texto que están asociados con este calle.|Black|  
|Modificador de acceso|el nivel de acceso de la clase \(`public` o `internal`\).|Public|  
|Atributos personalizados|Se utiliza para agregar atributos a la clase del código que se genera de este calle.|\<none\>|  
|genera derivado doble|Si `True`, una clase base y una clase parcial \(para admitir la personalización reemplaza a través\) se genera.  Para obtener más información, vea [Invalidar y ampliar clases generadas](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|tiene el constructor personalizado|Si `True`, un constructor personalizado proporcionado en el código fuente.  Para obtener más información, vea [Invalidar y ampliar clases generadas](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Modificador de herencia|Describe la clase de herencia de clases de código fuente que se genera de calle \(`none`, `abstract` o `sealed`\).|nada|  
|Base Calle|La clase base de este calle.|\(ninguno\)|  
|Name|El nombre de este calle.|nombre actual|  
|Espacio de nombres|El espacio de nombres que está asociado con este calle.|espacio de nombres actual|  
|Tipo de información sobre herramientas|Cómo la información sobre herramientas está definido \(`fixed`, `variable`, o `none`\).  Si `fixed`, el valor de la propiedad de `Fixed Tooltip Text` se utiliza; si `variable`, la información sobre herramientas se define en código personalizado.|\<none\>|  
|Notas|Notas informales que son asociado a este calle.|\<none\>|  
|Alineación|horizontal o alineación vertical.|Vertical|  
|alto inicial|El alto inicial de este calle, en pulgadas.  Aplicable únicamente a calles horizontales.|0|  
|ancho inicial|El ancho inicial de este calle, en pulgadas.  Aplicable únicamente a calles en paralelo.|0|  
|Color del texto de expone|Si `True`, el usuario puede establecer el color de un calle en el diseñador generado.  Para establecerla, haga clic con el botón secundario en la forma de calle y haga clic **agregue expuesto**.|False|  
|Descripción|Utilizado el documento el diseñador generado.|\<none\>|  
|Nombre para mostrar|El nombre que se mostrará en el diseñador generado para hacer referencia a esta clase de calle.|\<none\>|  
|texto de información sobre herramientas fijo|el texto que se utiliza para una información sobre herramientas fija.|\<none\>|  
|Palabra clave de Ayuda|La palabra clave que se utiliza para la ayuda de F1 de índice para este calle.|\<none\>|  
  
## Vea también  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/es-es/ca5e84cb-a315-465c-be24-76aa3df276aa)