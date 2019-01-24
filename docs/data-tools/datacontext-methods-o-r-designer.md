---
title: Métodos DataContext (Object Relational Designer)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c149f4e5-3b61-4c33-892e-3e26d47f3eeb
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 2279e938c9b2367ea917da8e3ec89196e39eaa27
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53880265"
---
# <a name="datacontext-methods-or-designer"></a>DataContext (Métodos) (Object Relational Designer)

<xref:System.Data.Linq.DataContext> métodos (en el contexto de la [LINQ to SQL Tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)) son métodos de la <xref:System.Data.Linq.DataContext> clase que se ejecutan procedimientos almacenados y funciones en una base de datos.

La clase <xref:System.Data.Linq.DataContext> es una clase de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] que actúa como una vía entre una base de datos de SQL Server y las clases de entidad de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] asignadas a esa base de datos. La clase <xref:System.Data.Linq.DataContext> contiene la información de la cadena de conexión y los métodos para realizar la conexión a una base de datos y manipular los datos de la base de datos. De forma predeterminada, la clase <xref:System.Data.Linq.DataContext> contiene varios métodos a los que se puede llamar, como el método <xref:System.Data.Linq.DataContext.SubmitChanges%2A> que envía los datos actualizados de las clases de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] a la base de datos. También se pueden crear métodos <xref:System.Data.Linq.DataContext> adicionales que se asignan a los procedimientos almacenados y funciones. En otras palabras, una llamada a estos métodos personalizados ejecuta el procedimiento almacenado o función en la base de datos a la que el <xref:System.Data.Linq.DataContext> método está asignado. Se pueden agregar métodos nuevos a la clase <xref:System.Data.Linq.DataContext> de la misma forma que se agregarían métodos para extender cualquier clase. Sin embargo, en las discusiones sobre <xref:System.Data.Linq.DataContext> métodos en el contexto de la **Object Relational Designer**, es el <xref:System.Data.Linq.DataContext> métodos que se asignan a los procedimientos almacenados y funciones que se analizan.

## <a name="methods-pane"></a>Panel de métodos

<xref:System.Data.Linq.DataContext> los métodos que se asignan a los procedimientos almacenados y funciones se muestran en el **métodos** panel de la **Object Relational Designer**. El panel **Métodos** es el situado junto al panel **Entidades** (la principal superficie de diseño). El **métodos** panel muestran todas <xref:System.Data.Linq.DataContext> métodos que ha creado mediante el **Object Relational Designer**. De forma predeterminada, el **métodos** panel está vacío; arrastre procedimientos almacenados o funciones desde **Explorador de servidores** o **Database Explorer** hasta la **Object Relational Designer**  crear <xref:System.Data.Linq.DataContext> métodos y rellenar el **métodos** panel. Para obtener más información, vea [Cómo: Crear métodos DataContext asignados a funciones y procedimientos almacenados (Object Relational Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md).

> [!NOTE]
> Abrir y cerrar el panel de métodos haciendo clic con el **Object Relational Designer** y, a continuación, haga clic en **ocultar panel métodos** o **Mostrar panel métodos**, o use el método abreviado de teclado  **CTRL**+**1**.

## <a name="two-types-of-datacontext-methods"></a>Dos tipos de métodos de DataContext

Los métodos de DataContext son los que se asignan a los procedimientos almacenados y funciones de la base de datos. Puede crear y agregar métodos DataContext en el **métodos** panel de la **Object Relational Designer**. Hay dos tipos distintos de métodos <xref:System.Data.Linq.DataContext>; los que devuelven uno o varios conjuntos de resultados y los que no:

- Métodos de <xref:System.Data.Linq.DataContext> que devuelven uno o varios conjuntos de resultados:

   Cree este tipo de método de <xref:System.Data.Linq.DataContext> cuando la aplicación solamente necesite ejecutar los procedimientos almacenados y funciones en la base de datos y devolver los resultados. Para obtener más información, vea [Cómo: Crear métodos DataContext asignados a procedimientos almacenados y funciones (Object Relational Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md), System.Data.Linq.ISingleResult\<T >, y <xref:System.Data.Linq.IMultipleResults>.

- Métodos de <xref:System.Data.Linq.DataContext> que no devuelven conjuntos de resultados, como Inserts, Updates y Deletes para una clase de entidad concreta.

   Cree este tipo de método de <xref:System.Data.Linq.DataContext> cuando la aplicación tenga que ejecutar los procedimientos almacenados en lugar de usar el comportamiento predeterminado de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] para guardar los datos modificados entre una clase de entidad y la base de datos. Para obtener más información, vea [Cómo: Asignación de procedimientos almacenados para realizar actualizaciones, inserciones y eliminaciones (Object Relational Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="return-types-of-datacontext-methods"></a>Tipos de valor devuelto de los métodos de DataContext

Cuando arrastre los procedimientos almacenados y funciones de **Explorador de servidores** o **Database Explorer** hasta la **Object Relational Designer**, el tipo de valor devuelto de generado <xref:System.Data.Linq.DataContext> método difiere según donde se coloque el elemento. Al colocar los elementos directamente en una clase de entidad existentes, crea un <xref:System.Data.Linq.DataContext> método con el tipo de valor devuelto de la clase de entidad; al colocar los elementos en un área vacía de la **Object Relational Designer** (en cualquiera de los paneles) crea un <xref:System.Data.Linq.DataContext> (método) que devuelve un tipo generado automáticamente. El tipo generado automáticamente tiene el nombre que coincida con el procedimiento almacenado o nombre de función y las propiedades, que se asignan a los campos devueltos por el procedimiento almacenado o función.

> [!NOTE]
> Se puede cambiar el tipo de valor devuelto de un método de <xref:System.Data.Linq.DataContext> después de agregarlo al panel de métodos. Para examinar o cambiar el tipo de valor devuelto de un método <xref:System.Data.Linq.DataContext>, selecciónelo y fíjese en la propiedad **Tipo devuelto** en la ventana **Propiedades**. Para obtener más información, vea [Cómo: Cambio del tipo de valor devuelto de un método DataContext (Object Relational Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

Objetos que se arrastran desde la base de datos a la superficie de Object Relational Designer se asignan automáticamente, según el nombre de los objetos de la base de datos. Si se arrastra al mismo objeto más de una vez, se agrega un número al final del nombre del nuevo diferenciar los nombres. Cuando los nombres de objetos de la base de datos contienen espacios o caracteres no admitidos en Visual Basic o C#, el espacio o el carácter no válido se sustituye por un carácter de subrayado.

## <a name="see-also"></a>Vea también

- [LINQ to SQL tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) (Herramientas LINQ to SQL en Visual Studio)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Procedimientos almacenados](/dotnet/framework/data/adonet/sql/linq/stored-procedures)
- [Cómo: Crear métodos DataContext asignados a funciones y procedimientos almacenados (Object Relational Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [Cómo: Asignar procedimientos almacenados para realizar actualizaciones, inserciones y eliminaciones (Object Relational Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)
- [Tutorial: Personalización del comportamiento de inserción, actualización y eliminación de clases de entidad](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [Tutorial: Creación de LINQ a las clases SQL (Object Relational Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)