---
title: (Object Relational Designer) de la herencia de clases de datos | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: af32653c-f4e6-4217-8c5a-e32b322b4918
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c361d35a4c5d6c4418a803b6bbba403e5571e1e2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47566042"
---
# <a name="data-class-inheritance-or-designer"></a>Herencia de clases de datos (Object Relational Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [(Object Relational Designer) de la herencia de clases de datos](https://docs.microsoft.com/visualstudio/data-tools/data-class-inheritance-o-r-designer).  
  
  
Al igual que otros objetos, las clases de [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] pueden usar la herencia y derivarse de otras clases. En el código, puede especificar las relaciones de la herencia entre los objetos declarando que una clase hereda de otra. En una base de datos, las relaciones de herencia se crean de varias maneras. El [!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]) admite el concepto de la herencia de tabla única normalmente implementada en los sistemas relacionales.  
  
 En la herencia de tabla única, hay una tabla de base de datos única que contiene columnas para las clases base y las derivadas. En el caso de datos relacionales, una columna discriminadora contiene el valor que determina la clase a la que pertenece un registro determinado. Por ejemplo, consideremos una tabla Persons que contiene todas las personas que trabajan en una compañía. Algunas personas son los empleados y otras son los directores. La tabla Persons contiene una columna denominada Type que tiene el valor 1 para directores y el valor 2 para empleados. La columna Type es la columna discriminadora. En este escenario, puede crear una subclase de empleados y rellenar la clase únicamente con los registros cuyo Type tiene el valor 2.  
  
 Al configurar la herencia de clases de entidad mediante el uso de la [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], arrastre la tabla única que contiene los datos de la herencia en el Diseñador de dos veces: una vez para cada clase en la jerarquía de herencia. Después de agregar las tablas al diseñador, conéctelas con un elemento de la herencia de la **Object Relational Designer** del cuadro de herramientas y, a continuación, establezca las cuatro propiedades de herencia en el **propiedades** ventana.  
  
## <a name="inheritance-properties"></a>Propiedades de herencia  
 En la tabla siguiente se muestran las propiedades de herencia y sus descripciones:  
  
|Propiedad|Descripción|  
|--------------|-----------------|  
|Propiedad Discriminator|La propiedad (asignada a la columna) que determina a qué clase pertenece el registro actual.|  
|Valor de discriminador de clase base|El valor (en la columna designada como la propiedad Discriminator) que determina que un registro es de la clase base.|  
|Valor de discriminador de clase derivada|El valor (en la propiedad designada como Discriminator) que determina que un registro es de la clase derivada.|  
|Predeterminado de herencia|La clase que se debe rellenar cuando el valor de la propiedad designada como la **propiedad Discriminator** no corresponderse con el **Base Class Discriminator Value** o la **clase derivada de Valor de discriminador**.|  
  
 La creación de un modelo de objetos que use la herencia y que corresponda a datos relacionales puede resultar un poco confusa. En este tema se proporciona información sobre los conceptos básicos y las propiedades individuales que se necesitan para configurar la herencia. Los temas siguientes proporcionan una explicación más clara de cómo configurar la herencia con el [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
|Tema|Descripción|  
|-----------|-----------------|  
|[Cómo: Configurar la herencia mediante Object Relational Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)|Describe cómo configurar las clases de entidad que usan la herencia de tabla única mediante el [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].|  
|[Tutorial: Crear clases de LINQ to SQL mediante la herencia de tabla única (Object Relational Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)|Proporciona instrucciones paso a paso sobre cómo configurar las clases de entidad que usan la herencia de tabla única mediante el [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].|  
  
## <a name="see-also"></a>Vea también  
 [LINQ to SQL Tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Tutorial: Crear clases LINQ to SQL (Object Relational Designer)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [Tutorial: Crear clases LINQ to SQL con herencia de tabla única (Object Relational Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)   
 [Introducción](http://msdn.microsoft.com/library/db8a557a-fef8-4f4f-bb91-8cff7250ee25)

