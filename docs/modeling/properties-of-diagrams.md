---
title: "Propiedades de los diagramas | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.dsltools.dsldesigner.dsldiagram"
helpviewer_keywords: 
  - "Lenguaje específico de dominio, diagrama"
ms.assetid: 00bba4b8-6aa6-4027-96cb-4f4c41a77d3c
caps.latest.revision: 25
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 25
---
# Propiedades de los diagramas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede establecer propiedades que especifican cómo los diagramas aparecerán en el diseñador generado.  Por ejemplo, puede especificar un color predeterminado para el texto del diagrama.  
  
 Para obtener más información, vea [Cómo: Definir lenguajes específicos de dominio](../modeling/how-to-define-a-domain-specific-language.md).  Para obtener más información sobre cómo utilizar estas propiedades, vea [Personalizar y ampliar lenguajes específicos de dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 La tabla siguiente se enumeran las propiedades de diagramas.  
  
|Propiedad.|Descripción|Default|  
|----------------|-----------------|-------------|  
|Color de relleno|El color de relleno del diagrama.|Blanco|  
|Color del texto|Color del texto que se muestra en el diagrama.|Black|  
|Modificador de acceso|El modificador de acceso de clase \(public o interno\).|Public|  
|Atributos personalizados|Se utiliza para agregar atributos a la clase generada del código.|\<none\>|  
|genera derivado doble|Si `True`, una clase base y una clase parcial \(para admitir la personalización reemplaza a través\) se genera.  Para obtener más información, vea [Invalidar y ampliar clases generadas](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|tiene el constructor personalizado|Si `True`, un constructor personalizado proporcionado en el código fuente.  Para obtener más información, vea [Invalidar y ampliar clases generadas](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Modificador de herencia|Describe la clase de herencia de clases de código fuente que se genera a partir del diagrama \(`none`, `abstract` o `sealed`\).|None|  
|diagrama base|la clase base de este diagrama.|\(ninguno\)|  
|Name|el nombre de este diagrama.|nombre actual|  
|Espacio de nombres|El espacio de nombres que está asociado con este diagrama.|espacio de nombres actual|  
|clase representada|La clase de dominio raíz que este diagrama representa.|Clase actual de la raíz si es necesario|  
|Notas|Notas informales que son asociado a este elemento.|\<none\>|  
|Color de relleno de expone como propiedad|Si `True`, el usuario puede establecer el color de relleno del diagrama del diseñador generado.  Para establecerla, haga clic con el botón secundario en la forma del diagrama y haga clic **agregue Explosed**.|False|  
|Color del texto de expone como propiedad|Si `True`, el usuario puede establecer el color del texto del diagrama en el diseñador generado.  Para establecerla, haga clic con el botón secundario en la forma del diagrama y haga clic **agregue Explosed**.|False|  
|Descripción|La descripción que se utiliza al documento el diseñador generado.|\<none\>|  
|Nombre para mostrar|El nombre que se mostrará en el diseñador generado para este diagrama.|\<none\>|  
|Palabra clave de Ayuda|La palabra clave que se utiliza para la ayuda de F1 de índice para este diagrama.|\<none\>|  
  
## Vea también  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/es-es/ca5e84cb-a315-465c-be24-76aa3df276aa)