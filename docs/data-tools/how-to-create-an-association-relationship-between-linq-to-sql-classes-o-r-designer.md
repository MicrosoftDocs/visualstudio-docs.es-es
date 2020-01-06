---
title: Relaciones entre las clases de LINQ to SQL (Object Relational Designer)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 56133e65-81f3-44c3-bc28-ffdd0671a0d2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: fb81cf17de86a11d2373f6a545b3efc78e65ada9
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586476"
---
# <a name="how-to-create-an-association-between-linq-to-sql-classes-or-designer"></a>Cómo: crear una asociación entre clases LINQ to SQL (Object Relational Designer)
Las asociaciones entre clases de entidades en [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] son similares a las relaciones entre tablas en una base de datos. Puede crear asociaciones entre clases de entidades mediante el cuadro de diálogo **Editor de asociaciones**.

Si utiliza el **Editor de asociaciones** para crear una asociación, deberá seleccionar una clase primaria y otra secundaria. La clase primaria es la clase de entidad que contiene la clave principal y la clase secundaria es la clase de entidad que contiene la clave externa. Por ejemplo, si se crearon clases de entidad que se asignan a las tablas `Northwind Customers` y `Orders`, la clase `Customer` sería la clase primaria y la clase `Order` sería la clase secundaria.

> [!NOTE]
> Al arrastrar tablas desde **Explorador de servidores** o **Explorador de bases de datos** al **Object Relational Designer** (Object Relational**Designer**), las asociaciones se crean automáticamente en función de las relaciones de clave externa existentes en la base de datos.

## <a name="association-properties"></a>Propiedades de la asociación
Una vez creada una asociación, al seleccionarla en el **Object Relational Designer**, se mostrarán algunas propiedades configurables en la ventana **Propiedades**. (La asociación es la línea entre las clases relacionadas). En la tabla siguiente se proporcionan descripciones de las propiedades de una asociación.

|La propiedad|Descripción|
|--------------|-----------------|
|**Cardinalidad**|Controla si la asociación es de uno a varios o de uno a uno.|
|**Propiedad secundaria**|Especifica si se debe crear una propiedad en el registro primario que es una colección o se debe hacer referencia a los registros secundarios en el lado de las claves externas de la asociación. Por ejemplo, en la asociación entre `Customer` y `Order`, si la **propiedad secundaria** está establecida en **true**, se crea una propiedad denominada `Orders` en la clase primaria.|
|**Propiedad primaria**|La propiedad de la clase secundaria que hace referencia a la clase primaria asociada. Por ejemplo, en la asociación entre `Customer` y `Order`, se crea una propiedad denominada `Customer` que hace referencia al cliente asociado para un pedido en la clase `Order`.|
|**Propiedades de participantes**|Muestra las propiedades de asociación y proporciona un botón de **puntos suspensivos** (...) que abre de nuevo el cuadro de diálogo **Editor de asociaciones**.|
|**Única**|Especifica si las columnas de destino externas tienen una restricción de unicidad.|

## <a name="to-create-an-association-between-entity-classes"></a>Para crear una asociación entre clases de entidad

1. Haga clic con el botón derecho en la clase de entidad que represente la clase primaria de la asociación, seleccione **Agregar** y después presione **Asociación**.

2. Compruebe que se haya seleccionado la **Clase primaria** correcta en el cuadro de diálogo **Editor de asociaciones**.

3. En el cuadro combinado, seleccione **Clase secundaria**.

4. Seleccione las **Propiedades de la asociación** que relacionan las clases. Por lo general, se asigna a la relación entre claves externas definida en la base de datos. Por ejemplo, en la Asociación `Customers` y `Orders`, las **propiedades** de la Asociación son las `CustomerID` de cada clase.

5. Haga clic en **Aceptar** para crear la asociación.

## <a name="see-also"></a>Vea también

- [LINQ to SQL tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) (Herramientas LINQ to SQL en Visual Studio)
- [Tutorial: crear clases de LINQ to SQL](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [DataContext methods (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md) (Métodos DataContext [Object Relational Designer])
- [Procedimiento para representar claves principales](/dotnet/framework/data/adonet/sql/linq/how-to-represent-primary-keys)
