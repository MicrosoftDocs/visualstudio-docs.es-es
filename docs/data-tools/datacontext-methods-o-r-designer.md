---
title: Métodos DataContext (Object Relational Designer)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c149f4e5-3b61-4c33-892e-3e26d47f3eeb
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: b8b9d322ea9c805b7fc1ce55dbf93b72b29958af
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "75586710"
---
# <a name="datacontext-methods-or-designer"></a>DataContext (Métodos) (Object Relational Designer)

<xref:System.Data.Linq.DataContext> los métodos (en el contexto de las [herramientas de LINQ to SQL en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)) son métodos de la <xref:System.Data.Linq.DataContext> clase que ejecutan procedimientos almacenados y funciones en una base de datos.

La clase <xref:System.Data.Linq.DataContext> es una clase de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] que actúa como una vía entre una base de datos de SQL Server y las clases de entidad de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] asignadas a esa base de datos. La clase <xref:System.Data.Linq.DataContext> contiene la información de la cadena de conexión y los métodos para realizar la conexión a una base de datos y manipular los datos de la base de datos. De forma predeterminada, la clase <xref:System.Data.Linq.DataContext> contiene varios métodos a los que se puede llamar, como el método <xref:System.Data.Linq.DataContext.SubmitChanges%2A> que envía los datos actualizados de las clases de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] a la base de datos. También se pueden crear métodos <xref:System.Data.Linq.DataContext> adicionales que se asignan a los procedimientos almacenados y funciones. En otras palabras, al llamar a estos métodos personalizados se ejecuta el procedimiento almacenado o la función en la base de datos a la que <xref:System.Data.Linq.DataContext> se asigna el método. Se pueden agregar métodos nuevos a la clase <xref:System.Data.Linq.DataContext> de la misma forma que se agregarían métodos para extender cualquier clase. Sin embargo, en las discusiones sobre <xref:System.Data.Linq.DataContext> los métodos en el contexto de **Object**Relational Designer, se trata de los <xref:System.Data.Linq.DataContext> métodos que se asignan a los procedimientos almacenados y a las funciones que se tratan.

## <a name="methods-pane"></a>Panel de métodos

<xref:System.Data.Linq.DataContext> los métodos que se asignan a los procedimientos almacenados y funciones se muestran en el panel de **métodos** de Object Relational **Designer**. El panel **Métodos** es el situado junto al panel **Entidades** (la principal superficie de diseño). En el panel **métodos** se enumeran todos los <xref:System.Data.Linq.DataContext> métodos que ha creado mediante Object Relational **Designer**. De forma predeterminada, el panel **métodos** está vacío; Arrastre los procedimientos almacenados o las funciones desde **Explorador de servidores** o **Explorador de bases de datos** a Object Relational **Designer** para crear <xref:System.Data.Linq.DataContext> métodos y rellenar el panel de **métodos** . Para obtener más información, vea [Cómo: crear métodos de DataContext asignados a funciones y procedimientos almacenados (Object](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)Relational Designer).

> [!NOTE]
> Abra y cierre el panel métodos; para ello, haga clic con el botón secundario en **Object Relational Designer** y, a continuación, haga clic en **ocultar el panel** métodos o **Mostrar métodos**, o use el método abreviado de teclado **Ctrl** + **1**.

## <a name="two-types-of-datacontext-methods"></a>Dos tipos de métodos de DataContext

Los métodos de DataContext son los que se asignan a los procedimientos almacenados y funciones de la base de datos. Puede crear y agregar métodos DataContext en el panel **métodos** de Object Relational **Designer**. Hay dos tipos distintos de métodos <xref:System.Data.Linq.DataContext>; los que devuelven uno o varios conjuntos de resultados y los que no:

- Métodos de <xref:System.Data.Linq.DataContext> que devuelven uno o varios conjuntos de resultados:

   Cree este tipo de método de <xref:System.Data.Linq.DataContext> cuando la aplicación solamente necesite ejecutar los procedimientos almacenados y funciones en la base de datos y devolver los resultados. Para obtener más información, vea [Cómo: crear métodos de DataContext asignados a funciones y procedimientos almacenados (Object](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)Relational Designer), System. Data. Linq. ISingleResult y \<T> <xref:System.Data.Linq.IMultipleResults> .

- Métodos de <xref:System.Data.Linq.DataContext> que no devuelven conjuntos de resultados, como Inserts, Updates y Deletes para una clase de entidad concreta.

   Cree este tipo de método de <xref:System.Data.Linq.DataContext> cuando la aplicación tenga que ejecutar los procedimientos almacenados en lugar de usar el comportamiento predeterminado de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] para guardar los datos modificados entre una clase de entidad y la base de datos. Para obtener más información, vea [Cómo: asignar procedimientos almacenados para realizar actualizaciones, inserciones y eliminaciones (Object](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)Relational Designer).

## <a name="return-types-of-datacontext-methods"></a>Tipos de valor devuelto de los métodos de DataContext

Al arrastrar procedimientos almacenados y funciones desde **Explorador de servidores** o **Explorador de bases de datos** a Object Relational **Designer**, el tipo de valor devuelto del <xref:System.Data.Linq.DataContext> método generado varía en función de dónde se coloque el elemento. Al colocar los elementos directamente en una clase de entidad existente, se crea un <xref:System.Data.Linq.DataContext> método con el tipo de valor devuelto de la clase de entidad; si se quitan elementos en un área vacía de Object Relational **Designer** (en cualquiera de los dos paneles), se crea un <xref:System.Data.Linq.DataContext> método que devuelve un tipo generado automáticamente. El tipo generado automáticamente tiene el nombre que coincide con el nombre de la función o el procedimiento almacenado, y las propiedades, que se asignan a los campos devueltos por el procedimiento almacenado o la función.

> [!NOTE]
> Se puede cambiar el tipo de valor devuelto de un método de <xref:System.Data.Linq.DataContext> después de agregarlo al panel de métodos. Para examinar o cambiar el tipo de valor devuelto de un método <xref:System.Data.Linq.DataContext>, selecciónelo y fíjese en la propiedad **Tipo devuelto** en la ventana **Propiedades**. Para obtener más información, vea [Cómo: cambiar el tipo de valor devuelto de un método DataContext (Object](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)Relational Designer).

Los objetos que se arrastran desde la base de datos hasta la superficie del diseñador de O/R se denominan automáticamente, según el nombre de los objetos de la base de datos. Si arrastra el mismo objeto más de una vez, se agrega un número al final del nuevo nombre que diferencia los nombres. Cuando los nombres de objetos de la base de datos contienen espacios o caracteres no admitidos en Visual Basic o C#, el espacio o el carácter no válido se sustituye por un carácter de subrayado.

## <a name="see-also"></a>Consulte también

- [Herramientas de LINQ to SQL en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [procedimientos almacenados](/dotnet/framework/data/adonet/sql/linq/stored-procedures)
- [Cómo: Crear métodos DataContext asignados a funciones y procedimientos almacenados (Object Relational Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [Cómo: Asignar procedimientos almacenados para realizar actualizaciones, inserciones y eliminaciones (Object Relational Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)
- [Tutorial: Personalizar el comportamiento de inserción, actualización y eliminación de las clases de entidad](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [Walkthrough: Creating LINQ to SQL classes (O-R Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md) (Tutorial: Crear clases de LINQ to SQL [Object Relational Designer])
