---
title: "Cómo: crear métodos DataContext asignados a procedimientos almacenados y funciones (Object Relational Designer) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e7ca32f1-50b3-48af-ad92-ceafd749296a
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: a162c9cb7cf7febf6e3b6e95e927a31b6591b027
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2017
---
# <a name="how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-or-designer"></a>Cómo: crear métodos DataContext asignados a procedimientos almacenados y funciones (Object Relational Designer)
Procedimientos almacenados y funciones que pueden agregarse a la [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] como <xref:System.Data.Linq.DataContext> métodos. Llamar al método y pasar los parámetros necesarios se ejecuta el procedimiento almacenado o función en la base de datos y devuelve los datos en el tipo de valor devuelto de la <xref:System.Data.Linq.DataContext> método. Para obtener información detallada acerca de <xref:System.Data.Linq.DataContext> métodos, vea [métodos DataContext (Object Relational Designer)](../data-tools/datacontext-methods-o-r-designer.md).  
  
> [!NOTE]
>  Los procedimientos almacenados también se pueden usar para invalidar el comportamiento predeterminado de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] en tiempo de ejecución para las inserciones, actualizaciones y eliminaciones cuando se guardan los cambios de las clases de entidad en una base de datos. Para obtener más información, consulte [Cómo: asignar procedimientos almacenados para realizar actualizaciones, inserciones y eliminaciones (Object Relational Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).  
  
## <a name="creating-datacontext-methods"></a>Crear métodos de DataContext  
 Puede crear <xref:System.Data.Linq.DataContext> métodos arrastrando procedimientos almacenan o funciones de **Server Explorer/Database Explorer** en el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
> [!NOTE]
>  El tipo de valor devuelto del método de <xref:System.Data.Linq.DataContext> generado difiere según la ubicación donde se coloque el procedimiento almacenado o la función en el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Si se coloca un elemento directamente en una clase de entidad existente, se crea un método de <xref:System.Data.Linq.DataContext> con el tipo de valor devuelto de la clase de entidad. Si se coloca un elemento en un área vacía del [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], se crea un método de <xref:System.Data.Linq.DataContext> que devuelve un tipo generado automáticamente. Puede cambiar el tipo de valor devuelto de un <xref:System.Data.Linq.DataContext> método después de agregarlo al panel de métodos. Para examinar o cambiar el tipo de valor devuelto de un <xref:System.Data.Linq.DataContext> método, selecciónelo y fíjese la **tipo de valor devuelto** propiedad en el **propiedades** ventana. Para obtener más información, consulte [Cómo: cambiar el tipo de valor devuelto de un método de DataContext (Object Relational Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### <a name="to-create-datacontext-methods-that-return-automatically-generated-types"></a>Para crear métodos de DataContext que devuelvan tipos generados automáticamente  
  
1.  En **Explorador de servidores**/**el Explorador de base de datos**, expanda la **procedimientos almacenados** nodo de la base de datos que está trabajando.  
  
2.  Busque el procedimiento almacenado que desee y arrástrelo hasta un área vacía del [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
     El <xref:System.Data.Linq.DataContext> método se crea con un tipo de valor devuelto generado automáticamente y aparece en el **métodos** panel.  
  
#### <a name="to-create-datacontext-methods-that-have-the-return-type-of-an-entity-class"></a>Para crear métodos de DataContext con el tipo de valor devuelto de una clase de entidad  
  
1.  En **Explorador de servidores**/**el Explorador de base de datos**, expanda la **procedimientos almacenados** nodo de la base de datos que está trabajando.  
  
2.  Busque el procedimiento almacenado que desee y arrástrelo hasta una clase de entidad existente en el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
     El <xref:System.Data.Linq.DataContext> método se crea con el tipo de valor devuelto de la clase de entidad seleccionada y aparece en el **métodos** panel.  
  
> [!NOTE]
>  Para obtener información acerca de cómo cambiar el tipo de valor devuelto de existente <xref:System.Data.Linq.DataContext> métodos, vea [Cómo: cambiar el tipo de valor devuelto de un método de DataContext (Object Relational Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).  
  
## <a name="see-also"></a>Vea también  
 [LINQ to SQL herramientas en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Métodos de DataContext (Object Relational Designer)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Tutorial: Crear clases LINQ to SQL](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)   
 [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)   
 [Introducción a LINQ en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [Cómo: Escribir consultas con LINQ en C#](http://msdn.microsoft.com/Library/45e47fcc-cfa1-4b72-b161-d038ae87bd23)