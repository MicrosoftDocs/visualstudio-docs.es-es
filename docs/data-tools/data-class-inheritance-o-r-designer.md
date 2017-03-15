---
title: "Herencia de clases de datos (Object Relational Designer) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: af32653c-f4e6-4217-8c5a-e32b322b4918
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Herencia de clases de datos (Object Relational Designer)
Al igual que otros objetos, las clases de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] pueden usar la herencia y derivarse de otras clases.En el código, puede especificar las relaciones de la herencia entre los objetos declarando que una clase hereda de otra.En una base de datos, las relaciones de herencia se crean de varias maneras.El [!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] \([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]\) admite el concepto de la herencia de tabla única normalmente implementada en los sistemas relacionales.  
  
 En la herencia de tabla única, hay una tabla de base de datos única que contiene columnas para las clases base y las derivadas.En el caso de datos relacionales, una columna discriminadora contiene el valor que determina la clase a la que pertenece un registro determinado.Por ejemplo, consideremos una tabla Persons que contiene todas las personas que trabajan en una compañía.Algunas personas son los empleados y otras son los directores.La tabla Persons contiene una columna denominada Type que tiene el valor 1 para directores y el valor 2 para empleados.La columna Type es la columna discriminadora.En este escenario, puede crear una subclase de empleados y rellenar la clase únicamente con los registros cuyo Type tiene el valor 2.  
  
 Al configurar la herencia en clases de entidad mediante el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], arrastre dos veces la tabla única que contiene los datos de la herencia hacia el diseñador: una vez por cada clase en la jerarquía de herencia.Después de agregar las tablas al diseñador, conéctelas con un elemento Herencia del cuadro de herramientas **Object Relational Designer** y, a continuación, establezca las cuatro propiedades de herencia en la ventana **Propiedades**.  
  
## Propiedades de herencia  
 En la tabla siguiente se muestran las propiedades de herencia y sus descripciones:  
  
|Propiedad|Descripción|  
|---------------|-----------------|  
|Propiedad Discriminator|La propiedad \(asignada a la columna\) que determina a qué clase pertenece el registro actual.|  
|Valor de discriminador de clase base|El valor \(en la columna designada como la propiedad Discriminator\) que determina que un registro es de la clase base.|  
|Valor de discriminador de clase derivada|El valor \(en la propiedad designada como Discriminator\) que determina que un registro es de la clase derivada.|  
|Predeterminado de herencia|La clase que se debería rellenar cuando el valor en la propiedad designada como la propiedad **Discriminator** no coincide con el **Valor de discriminador de clase base** ni con el **Valor de discriminador de clase derivada**.|  
  
 La creación de un modelo de objetos que use la herencia y que corresponda a datos relacionales puede resultar un poco confusa.En este tema se proporciona información sobre los conceptos básicos y las propiedades individuales que se necesitan para configurar la herencia.Los temas siguientes proporcionan una explicación más clara de cómo configurar la herencia con el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
|Tema|Descripción|  
|----------|-----------------|  
|[Cómo: Configurar herencia usando Object Relational Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)|Describe cómo configurar las clases de entidad que usan la herencia de tabla única mediante el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].|  
|[Tutorial: Crear clases de LINQ to SQL usando la herencia de tabla única \(Object Relational Designer\)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)|Proporciona instrucciones paso a paso sobre cómo configurar las clases de entidad que usan la herencia de tabla única mediante el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].|  
  
## Vea también  
 [Información general sobre Object Relational Designer](../Topic/LINQ%20to%20SQL%20Tools%20in%20Visual%20Studio1.md)   
 [Tutorial: Crear clases de LINQ to SQL \(Object Relational Designer\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [Tutorial: Crear clases de LINQ to SQL usando la herencia de tabla única \(Object Relational Designer\)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)   
 [Introducción](../Topic/Getting%20Started.md)