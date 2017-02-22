---
title: "Propiedades de las formas de imagen | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.dsltools.dsldesigner.selectimagedialog"
  - "vs.dsltools.dsldesigner.imageshape"
helpviewer_keywords: 
  - "Lenguaje específico de dominio, forma de imagen"
ms.assetid: 9ce00ccd-07f2-4640-ac96-2a60481d0d72
caps.latest.revision: 25
caps.handback.revision: 25
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Propiedades de las formas de imagen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede utilizar las formas de la imagen para especificar cómo las clases de dominio aparecen en un diseñador generado.  Defina una forma de imagen estableciendo la propiedad de `Image` de la clase en un archivo de imagen predefinido.  Se admiten los siguientes formatos:  
  
-   .gif  
  
-   .jpg  
  
-   .jpeg  
  
-   .bmp  
  
-   .wmf  
  
-   .emf  
  
-   png  
  
 De forma predeterminada, los archivos de recursos de diseñador, como archivos de imagen, se encuentran en la carpeta de **RECURSOS**en el proyecto de **DSL** .  
  
 Para obtener más información, vea [Cómo: Definir lenguajes específicos de dominio](../modeling/how-to-define-a-domain-specific-language.md).  Para obtener más información sobre cómo utilizar estas propiedades, vea [Personalizar y ampliar lenguajes específicos de dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 Las formas de la imagen tienen propiedades que se muestran en la tabla siguiente.  
  
|Propiedad.|Descripción|Default|  
|----------------|-----------------|-------------|  
|Color de relleno|el color de relleno de esta forma.|Blanco|  
|Modo de degradado de relleno|El modo de degradado de relleno de esta forma.|Horizontal|  
|tiene puntos de conexión predeterminados|Si `True`, la forma utiliza la parte superior, inferior, izquierdo, y los puntos de conexión correctos en el diseñador generado.|False|  
|Color|el contorno color de esta forma.|Black|  
|Estilo de guión de esquema|El estilo de guión del contorno de esta forma \(Solid, guión, punto, DashDot, DashDotDot, o personalizado\).|Sólido|  
|Grosor del contorno|El grosor del contorno de esta forma.|0.03125|  
|Color del texto|El color que se utiliza para los elementos decorator de texto que están asociados con esta forma.|Black|  
|Modificador de acceso|El modificador de acceso de la geometría \(public o interno\).|Public|  
|Atributos personalizados|Se utiliza para agregar atributos a la clase del código fuente se genera de esta forma.|\<none\>|  
|genera derivado doble|Si `True`, una clase base y una clase parcial \(para admitir la personalización reemplaza a través\) se genera.  Para obtener más información, vea [Invalidar y ampliar clases generadas](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|tiene el constructor personalizado|Si `True`, un constructor personalizado proporcionado en el código fuente.  Para obtener más información, vea [Invalidar y ampliar clases generadas](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Modificador de herencia|Describe la clase de herencia de clases de código fuente que se genera de la imagen \(`none`, `abstract` o `sealed`\).|nada|  
|Base la imagen|la clase base de esta forma.|\(ninguno\)|  
|Name|el nombre de esta forma.|nombre actual|  
|Espacio de nombres|El espacio de nombres que está asociado con esta forma.|espacio de nombres actual|  
|Tipo de información sobre herramientas|El lugar donde se define la información sobre herramientas \(corregido, variable, ni\).  Si se ha corregido, el valor de la propiedad de `Fixed Tooltip Text` se utiliza como la información sobre herramientas; si la variable, la información sobre herramientas se define en código personalizado.|nada|  
|Notas|Notas informales que son asociado a esta forma.|\<none\>|  
|alto inicial|el alto inicial de esta forma, en pulgadas.|1|  
|ancho inicial|el ancho inicial de esta forma, en pulgadas.|1.5|  
|color de relleno expuesto como propiedad<br /><br /> Modo expuesto degradado de relleno<br /><br /> contorno expuesto Color como propiedad<br /><br /> Estilo de guión expuesto de esquema como propiedad<br /><br /> Grosor expuesto de esquema como propiedad<br /><br /> Color del texto de expone|si `True`, el usuario puede establecer la propiedad dicha de una forma.  Para establecerla, haga clic con el botón secundario en la definición de la forma y haga clic **agregue expuesto**.|False|  
|Descripción|Utilizado el documento el diseñador generado.|\<none\>|  
|Nombre para mostrar|El nombre que se mostrará en el diseñador generado para esta forma.|\<none\>|  
|texto de información sobre herramientas fijo|el texto que se utiliza para una información sobre herramientas fija.|\<none\>|  
|Palabra clave de Ayuda|La palabra clave que se utiliza para la ayuda de F1 de índice para este elemento.|\<none\>|  
|Image|La ruta de acceso al archivo de imagen que se utiliza para esta forma.|\<none\>|  
  
## Vea también  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/es-es/ca5e84cb-a315-465c-be24-76aa3df276aa)