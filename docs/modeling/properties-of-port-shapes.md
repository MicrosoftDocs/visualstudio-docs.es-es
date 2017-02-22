---
title: "Propiedades de las formas de puerto | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.dsltools.dsldesigner.port"
helpviewer_keywords: 
  - "Lenguaje específico de dominio, forma de puerto"
ms.assetid: 9d69c4c1-4f72-4876-96b6-9b846e0495a4
caps.latest.revision: 21
caps.handback.revision: 21
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Propiedades de las formas de puerto
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede utilizar formas de puerto para representar clases de dominio en el diseñador generado.  
  
 Para obtener más información, vea [Cómo: Definir lenguajes específicos de dominio](../modeling/how-to-define-a-domain-specific-language.md).  Para obtener más información sobre cómo utilizar estas propiedades, vea [Personalizar y ampliar lenguajes específicos de dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 Las formas de puerto tienen propiedades que se muestran en la tabla siguiente.  
  
|Propiedad.|Descripción|Default|  
|----------------|-----------------|-------------|  
|Color de relleno|el color de relleno de esta forma.|Blanco|  
|Modo de degradado de relleno|El modo de degradado de relleno de esta forma.|Horizontal|  
|Geometry|la geometría de esta forma \(rectángulo, rectángulo redondeado, elipse, o círculo\).|Rectángulo|  
|tiene puntos de conexión predeterminados|Si `True`, la forma utiliza la parte superior, inferior, izquierdo, y los puntos de conexión correctos en el diseñador generado.|False|  
|Color|el contorno color de esta forma.|Black|  
|Estilo de guión de esquema|El estilo de guión del contorno de esta forma \(Solid, guión, punto, DashDot, DashDotDot, o personalizado\).|Sólido|  
|Grosor del contorno|El grosor del contorno de esta forma.|0.03125|  
|Color del texto|El color que se utiliza para los elementos decorator de texto que están asociados con esta forma.|Black|  
|Modificador de acceso|el nivel de acceso de la clase \(`public` o `internal`\).|Public|  
|Atributos personalizados|Se utiliza para agregar atributos a la clase del código fuente se genera de esta forma.|\<none\>|  
|genera derivado doble|Si `True`, una clase base y una clase parcial \(para admitir la personalización reemplaza a través\) se genera.  Para obtener más información, vea [Invalidar y ampliar clases generadas](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|tiene el constructor personalizado|Si `True`, un constructor personalizado proporcionado en el código fuente.  Para obtener más información, vea [Invalidar y ampliar clases generadas](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Modificador de herencia|Describe la clase de herencia de clases de código fuente que se genera de puerto \(`none`, `abstract` o `sealed`\).|nada|  
|puerto base|la clase base de esta forma.|\(ninguno\)|  
|Name|el nombre de esta forma.|nombre actual|  
|Espacio de nombres|El espacio de nombres que está asociado con esta forma.|espacio de nombres actual|  
|Tipo de información sobre herramientas|Cómo la información sobre herramientas está definido \(corregido, variable, ni\).  Si se ha corregido, el valor de la propiedad de `Fixed Tooltip Text` se utiliza como la información sobre herramientas; si la variable, la información sobre herramientas se define en código personalizado.|nada|  
|Notas|Notas informales que son asociado a esta forma.|\<none\>|  
|alto inicial|el alto inicial de esta forma, en pulgadas.|1|  
|ancho inicial|el ancho inicial de esta forma, en pulgadas.|1.5|  
|color de relleno expuesto como propiedad<br /><br /> Modo expuesto degradado de relleno<br /><br /> contorno expuesto Color como propiedad<br /><br /> Estilo de guión expuesto de esquema como propiedad<br /><br /> Grosor expuesto de esquema como propiedad<br /><br /> Color del texto de expone|si `True`, el usuario puede establecer la propiedad dicha de una forma.  Para establecerla, haga clic con el botón secundario en la definición de la forma y haga clic **agregue expuesto**.|False|  
|Descripción|Utilizado el documento el diseñador generado.|\<none\>|  
|Nombre para mostrar|El nombre que se mostrará en el diseñador generado para esta forma.|\<none\>|  
|Texto de información sobre herramientas fijo|el texto que se utiliza para una información sobre herramientas fija.|\<none\>|  
|Palabra clave de Ayuda|La palabra clave que se utiliza para la ayuda de F1 de índice para esta forma.|\<none\>|  
  
## Vea también  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/es-es/ca5e84cb-a315-465c-be24-76aa3df276aa)