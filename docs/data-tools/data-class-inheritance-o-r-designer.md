---
title: Herencia de clases de datos (Object Relational Designer)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: af32653c-f4e6-4217-8c5a-e32b322b4918
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 6c6b17ad38e9aae78975e43797931a326955712d
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36756742"
---
# <a name="data-class-inheritance-or-designer"></a>Herencia de clases de datos (Object Relational Designer)

Al igual que otros objetos, clases LINQ to SQL puede usar la herencia y derivarse de otras clases. En el código, puede especificar las relaciones de la herencia entre los objetos declarando que una clase hereda de otra. En una base de datos, las relaciones de herencia se crean de varias maneras. El **Object Relational Designer** (**Object Relational Designer**) admite el concepto de herencia de tabla única normalmente implementada en los sistemas relacionales.

En la herencia de tabla única, hay una tabla de base de datos única que contiene columnas para las clases base y las derivadas. En el caso de datos relacionales, una columna discriminadora contiene el valor que determina la clase a la que pertenece un registro determinado. Por ejemplo, considere un `Persons` tabla que contiene todos los usuarios trabajan en una compañía. Algunas personas son los empleados y otras son los directores. El `Persons` tabla contiene una columna denominada `Type` que tiene un valor de 1 para directores y el valor de 2 para los empleados. El `Type` es la columna discriminadora. En este escenario, puede crear una subclase de empleados y rellenar la clase únicamente con los registros que tienen un `Type` valor 2.

Al configurar la herencia de clases de entidad mediante el uso de la [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], arrastre la tabla única que contiene los datos de la herencia en el Diseñador de dos veces: una vez para cada clase en la jerarquía de herencia. Después de agregar las tablas al diseñador, conéctelas con un elemento de la herencia de la **Object Relational Designer** del cuadro de herramientas y, a continuación, establezca las cuatro propiedades de herencia en el **propiedades** ventana.

## <a name="inheritance-properties"></a>Propiedades de herencia

En la tabla siguiente se muestran las propiedades de herencia y sus descripciones:

|Propiedad|Descripción|
|--------------|-----------------|
|**Propiedad discriminator**|La propiedad (asignada a la columna) que determina a qué clase pertenece el registro actual.|
|**Valor de discriminador de clase base**|El valor (en la columna designada como la **propiedad Discriminator**) que determina que es un registro de la clase base.|
|**Valor de discriminador de clase derivada**|El valor (en la propiedad designada como la **propiedad Discriminator**) que determina que es un registro de la clase derivada.|
|**Herencia predeterminada**|La clase que se rellena cuando el valor de la propiedad designada como la **propiedad Discriminator** no corresponderse con el **Base Class Discriminator Value** o la **clase derivada de Valor de discriminador**.|

La creación de un modelo de objetos que use la herencia y que corresponda a datos relacionales puede resultar un poco confusa. En este tema se proporciona información sobre los conceptos básicos y las propiedades individuales que se necesitan para configurar la herencia. Los temas siguientes proporcionan una explicación más clara de cómo configurar la herencia con la **Object Relational Designer**.

|Tema|Descripción|
|-----------|-----------------|
|[Cómo: configurar la herencia mediante Object Relational Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)|Describe cómo configurar las clases de entidad que usan la herencia de tabla única mediante el uso de la **Object Relational Designer**.|
|[Tutorial: Creación de LINQ a las clases SQL mediante la herencia de tabla única (Object Relational Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)|Proporciona instrucciones paso a paso sobre cómo configurar las clases de entidad que usan la herencia de tabla única mediante el uso de la **Object Relational Designer**.|

## <a name="see-also"></a>Vea también

- [LINQ to SQL tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Tutorial: Creación de LINQ a las clases SQL (Object Relational Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [Tutorial: Creación de LINQ a las clases SQL mediante la herencia de tabla única (Object Relational Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
- [Introducción](/dotnet/framework/data/adonet/sql/linq/getting-started)