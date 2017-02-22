---
title: "Propiedades de los conectores | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Lenguaje específico de dominio, conectores"
ms.assetid: b1f24e8d-cdd7-4a5d-af37-1038f43b45c7
caps.latest.revision: 21
caps.handback.revision: 21
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Propiedades de los conectores
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Los conectores representan relaciones de dominio en un diseñador generado.  
  
 Para obtener más información, vea [Cómo: Definir lenguajes específicos de dominio](../modeling/how-to-define-a-domain-specific-language.md).  Para obtener más información sobre cómo utilizar estas propiedades, vea [Personalizar y ampliar lenguajes específicos de dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 Los conectores tienen propiedades que se muestran en la tabla siguiente.  
  
|Propiedad.|Descripción|Default|  
|----------------|-----------------|-------------|  
|Color|Color del conector.|Black|  
|estilo de guión|El estilo de guión para la línea para este conector \(Solid, guión, punto, DashDot, DashDotDot, o personalizado\).|Sólido|  
|Estilo del extremo de origen|El origen finaliza el estilo para este conector \(HollowArrow, EmptyArrow, FilledArrow, EmptyDiamond, FilledDiamond, None\).|None|  
|Estilo de final de destino|El destino finaliza el estilo para este conector \(HollowArrow, EmptyArrow, FilledArrow, EmptyDiamond, FilledDiamond, None\).|None|  
|Color del texto|El color que se utiliza para los elementos decorator de texto que están asociados con este conector.|Black|  
|Thickness|el grosor de la línea para este conector, medida en pulgadas.|0.03125|  
|Modificador de acceso|el nivel de acceso de la clase \(`public` o `internal`\).|Public|  
|Atributos personalizados|Se utiliza para agregar atributos a la clase del código fuente generado con este conector.|\<none\>|  
|genera derivado doble|Si `True`, una clase base y una clase parcial \(para admitir la personalización reemplaza a través\) se genera.  Para obtener más información, vea [Invalidar y ampliar clases generadas](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|tiene el constructor personalizado|Si `True`, un constructor personalizado proporcionado en el código fuente.  Para obtener más información, vea [Invalidar y ampliar clases generadas](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Modificador de herencia|Describe la clase de herencia de clases de código fuente que se genera el conector \(`none`, `abstract` o `sealed`\).|nada|  
|base el conector|la clase base de este conector.|\(ninguno\)|  
|Name|el nombre de este conector.|nombre actual|  
|Espacio de nombres|El espacio de nombres que está asociado con este conector.|espacio de nombres actual|  
|Tipo de información sobre herramientas|Cómo la información sobre herramientas está definido \(corregido, variable, ni\).  Si se ha corregido, el valor de la propiedad de `Fixed Tooltip Text` se utiliza como la información sobre herramientas; si la variable, la información sobre herramientas se define en código personalizado.|\<none\>|  
|Notas|Notas informales que son asociado a este conector.|\<none\>|  
|Estilo de enrutamiento|el estilo que se utiliza para distribuir el conector.  un conector de `Rectilinear` crea en ángulo recto gira como sea necesario; un conector de `Straight` no.|rectilíneo|  
|color expuesto como propiedad<br /><br /> estilo de guión expuesto como propiedad<br /><br /> grosor expuesto como propiedad<br /><br /> Color del texto de expone|si `True`, el usuario puede establecer la propiedad dicha de una forma.  Para establecerla, haga clic con el botón secundario en la definición de la forma y haga clic **agregue expuesto**.|False|  
|Descripción|Utilizado el documento el diseñador generado.|\<none\>|  
|Nombre para mostrar|El nombre que se mostrará en el diseñador generado para este conector.|\<none\>|  
|texto de información sobre herramientas fijo|el texto que se utiliza para una información sobre herramientas fija.|\<none\>|  
|Palabra clave de Ayuda|La palabra clave que se utiliza para la ayuda de F1 de índice para este elemento.|\<none\>|  
  
## Vea también  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/es-es/ca5e84cb-a315-465c-be24-76aa3df276aa)