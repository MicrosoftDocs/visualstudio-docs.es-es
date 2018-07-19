---
title: Cómo crear una relación entre clases LINQ to SQL mediante Object Relational Designer
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 56133e65-81f3-44c3-bc28-ffdd0671a0d2
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: d247603e14f431e44aa7c1589ba2ecd7463fac02
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089534"
---
# <a name="how-to-create-an-association-between-linq-to-sql-classes-or-designer"></a>Cómo: crear una asociación entre clases LINQ to SQL (Object Relational Designer)
Las asociaciones entre clases de entidades en [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] son similares a las relaciones entre tablas en una base de datos. Puede crear asociaciones entre las clases de entidad mediante el **Editor de asociaciones** cuadro de diálogo.

Debe seleccionar una clase primaria y otra secundaria cuando se usa el **Editor de asociaciones** cuadro de diálogo para crear una asociación. La clase primaria es la clase de entidad que contiene la clave principal y la clase secundaria es la clase de entidad que contiene la clave externa. Por ejemplo, si se crearon clases de entidad que se asignan a la `Northwind Customers` y `Orders` tablas, el `Customer` clase sería la clase primaria y la `Order` clase sería la clase secundaria.

> [!NOTE]
>  Al arrastrar las tablas de **Explorador de servidores** o **Database Explorer** hasta la **Object Relational Designer** (**Object Relational Designer**), las asociaciones se crean automáticamente en función de las relaciones de clave externa existentes en la base de datos.

## <a name="association-properties"></a>Propiedades de la asociación
Después de crear una asociación, al seleccionar la asociación en el **Object Relational Designer**, hay algunas propiedades configurables en el **propiedades** ventana. (La asociación es la línea entre las clases relacionadas). En la tabla siguiente, se proporcionan descripciones de las propiedades de una asociación.

|Propiedad|Descripción|
|--------------|-----------------|
|**cardinalidad**|Controla si la asociación es de uno a varios o de uno a uno.|
|**Propiedad secundaria**|Especifica si se debe crear una propiedad en el registro primario que es una colección o se debe hacer referencia a los registros secundarios en el lado de las claves externas de la asociación. Por ejemplo, en la asociación entre `Customer` y `Order`, si la **propiedad secundaria** está establecido en **True**, una propiedad denominada `Orders` se crea en la clase primaria.|
|**Propiedad primaria**|La propiedad de la clase secundaria que hace referencia a la clase primaria asociada. Por ejemplo, en la asociación entre `Customer` y `Order`, una propiedad denominada `Customer` que hace referencia al cliente asociado para un pedido se crea en el `Order` clase.|
|**Propiedades de participantes**|Muestra las propiedades de asociación y proporciona un **puntos suspensivos** botón (…) que abre de nuevo el **Editor de asociaciones** cuadro de diálogo.|
|**único**|Especifica si las columnas de destino externas tienen una restricción de unicidad.|

## <a name="to-create-an-association-between-entity-classes"></a>Para crear una asociación entre clases de entidad

1.  Haga clic en la clase de entidad que representa la clase primaria de la asociación, seleccione **agregar**y, a continuación, haga clic en **asociación**.

2.  Compruebe que el valor correcto **clase primaria** está seleccionado en el **Editor de asociaciones** cuadro de diálogo.

3.  Seleccione el **clase secundaria** en el cuadro combinado.

4.  Seleccione el **propiedades de la asociación** que relacionan las clases. Por lo general, se asigna a la relación entre claves externas definida en la base de datos. Por ejemplo, en el `Customers` y `Orders` asociación, el **propiedades de la asociación** son el `CustomerID` para cada clase.

5.  Haga clic en **Aceptar** para crear la asociación.

## <a name="see-also"></a>Vea también

- [LINQ to SQL tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Tutorial: Creación de LINQ a las clases SQL](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Métodos DataContext (Object Relational Designer)](../data-tools/datacontext-methods-o-r-designer.md)
- [Cómo: representar claves principales](/dotnet/framework/data/adonet/sql/linq/how-to-represent-primary-keys)