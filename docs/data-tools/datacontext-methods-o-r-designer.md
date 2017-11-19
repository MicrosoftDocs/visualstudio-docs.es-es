---
title: "Métodos de DataContext (Object Relational Designer) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c149f4e5-3b61-4c33-892e-3e26d47f3eeb
caps.latest.revision: "5"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: bc162882e8cece08a2688ccc73a674a9ab6e0fce
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="datacontext-methods-or-designer"></a>DataContext (Métodos) (Object Relational Designer)
<xref:System.Data.Linq.DataContext>métodos (en el contexto de la [LINQ to SQL Tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)) son métodos de la <xref:System.Data.Linq.DataContext> clase que se ejecutan procedimientos almacenados y funciones en una base de datos.  
  
 La clase <xref:System.Data.Linq.DataContext> es una clase de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] que actúa como una vía entre una base de datos de SQL Server y las clases de entidad de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] asignadas a esa base de datos. La clase <xref:System.Data.Linq.DataContext> contiene la información de la cadena de conexión y los métodos para realizar la conexión a una base de datos y manipular los datos de la base de datos. De forma predeterminada, la clase <xref:System.Data.Linq.DataContext> contiene varios métodos a los que se puede llamar, como el método <xref:System.Data.Linq.DataContext.SubmitChanges%2A> que envía los datos actualizados de las clases de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] a la base de datos. También puede crear más <xref:System.Data.Linq.DataContext> métodos que se asignan a los procedimientos almacenados y funciones. Es decir, al llamar a estos métodos personalizados, se ejecutará el procedimiento almacenado o la función en la base de datos a la que está asignado el método de <xref:System.Data.Linq.DataContext>. Se pueden agregar métodos nuevos a la clase <xref:System.Data.Linq.DataContext> de la misma forma que se agregarían métodos para extender cualquier clase. Sin embargo, en las discusiones sobre <xref:System.Data.Linq.DataContext> métodos en el contexto de la [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], es el <xref:System.Data.Linq.DataContext> métodos que se asignan a los procedimientos almacenados y funciones que se trata de un.  
  
## <a name="methods-pane"></a>Panel de métodos  
 Los métodos de <xref:System.Data.Linq.DataContext> que se asignan a los procedimientos almacenados y funciones se muestran en el panel de métodos del [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. El panel de métodos es el panel en el lateral de la **entidades** panel (la superficie de diseño principal). El panel de métodos muestra todos los <xref:System.Data.Linq.DataContext> métodos que han creado con la [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. De forma predeterminada, el panel de métodos está vacío; Arrastre los procedimientos almacenados o funciones desde **Explorador de servidores**/**el Explorador de base de datos** en el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] crear <xref:System.Data.Linq.DataContext> métodos y rellenar el panel de métodos. Para obtener más información, consulte [Cómo: métodos de DataContext crear asignados a procedimientos almacenados y funciones (Object Relational Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md).  
  
> [!NOTE]
>  Abrir y cerrar el panel de métodos haciendo clic en el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] y, a continuación, haga clic en **ocultar panel métodos** o **Mostrar panel métodos**, o utilice el método abreviado de teclado CTRL + 1.  
  
## <a name="two-types-of-datacontext-methods"></a>Dos tipos de métodos de DataContext  
 Los métodos de DataContext son los que se asignan a los procedimientos almacenados y funciones de la base de datos. Puede crear y agregar métodos DataContext en el panel de métodos de [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Hay dos tipos distintos de <xref:System.Data.Linq.DataContext> métodos; los que devuelven uno o varios conjuntos de resultados y los que no lo hacen:  
  
-   Métodos de <xref:System.Data.Linq.DataContext> que devuelven uno o varios conjuntos de resultados:  
  
     Cree este tipo de método de <xref:System.Data.Linq.DataContext> cuando la aplicación solamente necesite ejecutar los procedimientos almacenados y funciones en la base de datos y devolver los resultados. Para obtener más información, consulte [Cómo: métodos de DataContext crear asignados a procedimientos almacenados y funciones (Object Relational Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md), System.Data.Linq.ISingleResult\<T >, y <xref:System.Data.Linq.IMultipleResults>.  
  
-   Métodos de <xref:System.Data.Linq.DataContext> que no devuelven conjuntos de resultados, como Inserts, Updates y Deletes para una clase de entidad concreta.  
  
     Cree este tipo de <xref:System.Data.Linq.DataContext> método cuando la aplicación tiene que ejecutar procedimientos almacenados en lugar de utilizar el valor predeterminado [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] modificar el comportamiento para guardar datos entre una clase de entidad y la base de datos. Para obtener más información, consulte [Cómo: asignar procedimientos almacenados para realizar actualizaciones, inserciones y eliminaciones (Object Relational Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).  
  
## <a name="return-types-of-datacontext-methods"></a>Tipos de valor devuelto de los métodos de DataContext  
 Al arrastrar los procedimientos almacenados y funciones de **Explorador de servidores**/**el Explorador de base de datos** en el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], el tipo de valor devuelto de generado <xref:System.Data.Linq.DataContext> difiere del método Dependiendo de dónde colocar el elemento. Al colocar los elementos directamente en una clase de entidad existente se crea un <xref:System.Data.Linq.DataContext> método con el tipo de valor devuelto de la clase de entidad; al colocar los elementos en un área vacía de la [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] (en cualquiera de los paneles) crea un <xref:System.Data.Linq.DataContext> método que devuelva una tipo generado automáticamente. El tipo generado automáticamente coincide con el nombre del procedimiento almacenado o de la función y sus propiedades se asignan a los campos devueltos por el procedimiento almacenado o la función.  
  
> [!NOTE]
>  Se puede cambiar el tipo de valor devuelto de un método de <xref:System.Data.Linq.DataContext> después de agregarlo al panel de métodos. Para examinar o cambiar el tipo de valor devuelto de un <xref:System.Data.Linq.DataContext> método, selecciónelo y fíjese la **tipo de valor devuelto** propiedad en el **propiedades** ventana. Para obtener más información, consulte [Cómo: cambiar el tipo de valor devuelto de un método de DataContext (Object Relational Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).  
  
 Los objetos que se arrastran desde la base de datos a la superficie de Object Relational Designer reciben automáticamente un nombre basado en el nombre de los objetos de la base de datos. Si arrastra el mismo objeto más de una vez, se anexa un número al final del nuevo nombre para diferenciar los nombres. Cuando los nombres de objetos de la base de datos contienen espacios o caracteres no admitidos en Visual Basic o C#, el espacio o el carácter no válido se sustituye por un carácter de subrayado.  
  
## <a name="see-also"></a>Vea también  
 [LINQ to SQL herramientas en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)   
 [Procedimientos almacenados](/dotnet/framework/data/adonet/sql/linq/stored-procedures)   
 [Cómo: crear métodos DataContext asignados a procedimientos almacenados y funciones (Object Relational Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)   
 [Cómo: asignar procedimientos almacenados para realizar actualizaciones, inserciones y eliminaciones (Object Relational Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [Tutorial: Personalizar la instrucción insert, update y delete de comportamiento de las clases de entidad](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)   
 [Tutorial: Crear clases LINQ to SQL (Object Relational Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)