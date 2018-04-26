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
ms.openlocfilehash: c1ed71ad820e6e55d05bc7cc6c7bf62b45f58f55
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="data-class-inheritance-or-designer"></a>Herencia de clases de datos (Object Relational Designer)

Al igual que otros objetos, las clases de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] pueden usar la herencia y derivarse de otras clases. En el código, puede especificar las relaciones de la herencia entre los objetos declarando que una clase hereda de otra. En una base de datos, las relaciones de herencia se crean de varias maneras. El [!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] ([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]) admite el concepto de la herencia de tabla única normalmente implementada en los sistemas relacionales.

En la herencia de tabla única, hay una tabla de base de datos única que contiene columnas para las clases base y las derivadas. En el caso de datos relacionales, una columna discriminadora contiene el valor que determina la clase a la que pertenece un registro determinado. Por ejemplo, consideremos una tabla Persons que contiene todas las personas que trabajan en una compañía. Algunas personas son los empleados y otras son los directores. La tabla Persons contiene una columna denominada Type que tiene el valor 1 para directores y el valor 2 para empleados. La columna Type es la columna discriminadora. En este escenario, puede crear una subclase de empleados y rellenar la clase únicamente con los registros cuyo Type tiene el valor 2.

Al configurar la herencia de clases de entidad mediante el uso de la [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], arrastre la tabla única que contiene los datos de la herencia hacia el diseñador dos veces: una vez para cada clase de la jerarquía de herencia. Después de agregar las tablas al diseñador, conéctelas con un elemento de la herencia de la **Object Relational Designer** cuadro de herramientas y, a continuación, establezca las cuatro propiedades de herencia en el **propiedades** ventana.

## <a name="inheritance-properties"></a>Propiedades de herencia

En la tabla siguiente se muestran las propiedades de herencia y sus descripciones:

|Propiedad|Descripción|
|--------------|-----------------|
|Propiedad Discriminator|La propiedad (asignada a la columna) que determina a qué clase pertenece el registro actual.|
|Valor de discriminador de clase base|El valor (en la columna designada como la propiedad Discriminator) que determina que un registro es de la clase base.|
|Valor de discriminador de clase derivada|El valor (en la propiedad designada como Discriminator) que determina que un registro es de la clase derivada.|
|Predeterminado de herencia|La clase que se debería rellenar cuando el valor de la propiedad designada como la **propiedad Discriminator** no coincide con el **valor de discriminador de clase Base** o la **clase derivada de Valor de discriminador**.|

La creación de un modelo de objetos que use la herencia y que corresponda a datos relacionales puede resultar un poco confusa. En este tema se proporciona información sobre los conceptos básicos y las propiedades individuales que se necesitan para configurar la herencia. Los temas siguientes proporcionan una explicación más clara de cómo configurar la herencia con el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].

|Tema|Descripción|
|-----------|-----------------|
|[Cómo: configurar la herencia utilizando Object Relational Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)|Describe cómo configurar las clases de entidad que usan la herencia de tabla única mediante el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].|
|[Tutorial: Crear clases LINQ to SQL mediante la herencia de tabla única (Object Relational Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)|Proporciona instrucciones paso a paso sobre cómo configurar las clases de entidad que usan la herencia de tabla única mediante el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].|

## <a name="see-also"></a>Vea también

- [Herramientas LINQ to SQL en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Tutorial: Crear clases LINQ to SQL (Object Relational Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [Tutorial: Crear clases LINQ to SQL mediante la herencia de tabla única (Object Relational Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
- [Introducción](/dotnet/framework/data/adonet/sql/linq/getting-started)