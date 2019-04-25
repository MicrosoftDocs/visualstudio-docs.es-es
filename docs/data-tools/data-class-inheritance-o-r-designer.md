---
title: Herencia de clases de datos (Object Relational Designer)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: af32653c-f4e6-4217-8c5a-e32b322b4918
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: a8df3d39e44bf1d40f3abfd4d6218d2c9a72b690
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55935685"
---
# <a name="data-class-inheritance-or-designer"></a>Herencia de clases de datos (Object Relational Designer)

Al igual que otros objetos, clases LINQ to SQL puede usar la herencia y derivarse de otras clases. En el código, puede especificar las relaciones de la herencia entre los objetos declarando que una clase hereda de otra. En una base de datos, las relaciones de herencia se crean de varias maneras. El **Object Relational Designer** (**Object Relational Designer**) admite el concepto de herencia de tabla única normalmente implementada en los sistemas relacionales.

En la herencia de tabla única, hay una tabla de base de datos única que contiene columnas para las clases base y las derivadas. En el caso de datos relacionales, una columna discriminadora contiene el valor que determina la clase a la que pertenece un registro determinado. Por ejemplo, considere un `Persons` tabla que contiene todos los usuarios trabajan en una compañía. Algunas personas son los empleados y otras son los directores. El `Persons` tabla contiene una columna denominada `Type` que tiene un valor de 1 para directores y el valor de 2 para los empleados. El `Type` es la columna discriminadora. En este escenario, puede crear una subclase de empleados y rellenar la clase únicamente con los registros que tienen un `Type` valor 2.

Al configurar la herencia en clases de entidad mediante el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], arrastre dos veces la tabla única que contiene los datos de la herencia hacia el diseñador: una vez por cada clase en la jerarquía de herencia. Después de agregar las tablas al diseñador, conéctelas con un elemento Herencia del cuadro de herramientas **Object Relational Designer** y después establezca las cuatro propiedades de herencia en la ventana **Propiedades**.

## <a name="inheritance-properties"></a>Propiedades de herencia

En la tabla siguiente se muestran las propiedades de herencia y sus descripciones:

|Propiedad.|Descripción|
|--------------|-----------------|
|**Propiedad Discriminator**|La propiedad (asignada a la columna) que determina a qué clase pertenece el registro actual.|
|**Valor de discriminador de clase base**|Valor (en la columna designada como la **propiedad Discriminator**) que determina que un registro es de la clase base.|
|**Valor de discriminador de clase derivada**|Valor (en la propiedad designada como **propiedad Discriminator**) que determina que un registro es de la clase derivada.|
|**Predeterminado de herencia**|La clase que se rellena cuando el valor de la propiedad designada como la **propiedad Discriminator** no corresponderse con el **Base Class Discriminator Value** o la **clase derivada de Valor de discriminador**.|

La creación de un modelo de objetos que use la herencia y que corresponda a datos relacionales puede resultar un poco confusa. En este tema se proporciona información sobre los conceptos básicos y las propiedades individuales que se necesitan para configurar la herencia. Los temas siguientes proporcionan una explicación más clara de cómo configurar la herencia con la **Object Relational Designer**.

|Tema|Descripción|
|-----------|-----------------|
|[Cómo: Configurar la herencia mediante Object Relational Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)|Describe cómo configurar las clases de entidad que usan la herencia de tabla única mediante el uso de la **Object Relational Designer**.|
|[Tutorial: Creación de clases LINQ to SQL mediante la herencia de tabla única (Object Relational Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)|Proporciona instrucciones paso a paso sobre cómo configurar las clases de entidad que usan la herencia de tabla única mediante el uso de la **Object Relational Designer**.|

## <a name="see-also"></a>Vea también

- [LINQ to SQL tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) (Herramientas LINQ to SQL en Visual Studio)
- [Walkthrough: Creating LINQ to SQL classes (O-R Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md) (Tutorial: Crear clases de LINQ to SQL [Object Relational Designer])
- [Tutorial: Creación de clases LINQ to SQL mediante la herencia de tabla única (Object Relational Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
- [Introducción](/dotnet/framework/data/adonet/sql/linq/getting-started)