---
title: Herencia de clases de datos (Object Relational Designer)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: af32653c-f4e6-4217-8c5a-e32b322b4918
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 7172c868780aec61de8688614fbb93627dc23bf5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85462400"
---
# <a name="data-class-inheritance-or-designer"></a>Herencia de clases de datos (Object Relational Designer)

Al igual que otros objetos, las clases de LINQ to SQL pueden utilizar la herencia y derivarse de otras clases. En el código, puede especificar las relaciones de la herencia entre los objetos declarando que una clase hereda de otra. En una base de datos, las relaciones de herencia se crean de varias maneras. El **Object Relational Designer** (**Object**Relational Designer) admite el concepto de herencia de tabla única, ya que se suele implementar en sistemas relacionales.

En la herencia de tabla única, hay una tabla de base de datos única que contiene columnas para las clases base y las derivadas. En el caso de datos relacionales, una columna discriminadora contiene el valor que determina la clase a la que pertenece un registro determinado. Por ejemplo, considere una `Persons` tabla que contiene todos los empleados de una empresa. Algunas personas son los empleados y otras son los directores. La `Persons` tabla contiene una columna denominada `Type` que tiene un valor de 1 para los administradores y un valor de 2 para los empleados. La `Type` columna es la columna discriminadora. En este escenario, puede crear una subclase de empleados y rellenar la clase únicamente con los registros que tienen un `Type` valor de 2.

Al configurar la herencia en clases de entidad mediante el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], arrastre dos veces la tabla única que contiene los datos de la herencia hacia el diseñador: una vez por cada clase en la jerarquía de herencia. Después de agregar las tablas al diseñador, conéctelas con un elemento Herencia del cuadro de herramientas **Object Relational Designer** y después establezca las cuatro propiedades de herencia en la ventana **Propiedades**.

## <a name="inheritance-properties"></a>Propiedades de herencia

En la tabla siguiente se muestran las propiedades de herencia y sus descripciones:

|Propiedad|Descripción|
|--------------|-----------------|
|**Propiedad Discriminator**|La propiedad (asignada a la columna) que determina a qué clase pertenece el registro actual.|
|**Valor de discriminador de clase base**|El valor (en la columna designada como la **propiedad Discriminator**) que determina que un registro es de la clase base.|
|**Valor de discriminador de clase derivada**|El valor (en la propiedad designada como la **propiedad Discriminator**) que determina que un registro es de la clase derivada.|
|**Predeterminado de herencia**|La clase que se rellena cuando el valor de la propiedad designada como **propiedad de discriminador** no coincide con el valor de **discriminador de clase base** o el **valor de discriminador de clase derivada**.|

La creación de un modelo de objetos que use la herencia y que corresponda a datos relacionales puede resultar un poco confusa. En este tema se proporciona información sobre los conceptos básicos y las propiedades individuales que se necesitan para configurar la herencia. En los temas siguientes se proporciona una explicación más clara de cómo configurar la herencia con Object Relational **Designer**.

|Tema|Descripción|
|-----------|-----------------|
|[Cómo: Configurar la herencia mediante Object Relational Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)|Describe cómo configurar las clases de entidad que usan la herencia de tabla única mediante **Object**Relational Designer.|
|[Tutorial: crear clases de LINQ to SQL mediante la herencia de tabla única (Object Relational Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)|Proporciona instrucciones paso a paso sobre cómo configurar las clases de entidad que usan la herencia de tabla única mediante Object Relational **Designer**.|

## <a name="see-also"></a>Vea también

- [Herramientas de LINQ to SQL en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Walkthrough: Creating LINQ to SQL classes (O-R Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md) (Tutorial: Crear clases de LINQ to SQL [Object Relational Designer])
- [Tutorial: crear clases de LINQ to SQL mediante la herencia de tabla única (Object Relational Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
- [Introducción](/dotnet/framework/data/adonet/sql/linq/getting-started)