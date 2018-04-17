---
title: 'Cómo: cambiar el tipo de valor devuelto de un método de DataContext (Object Relational Designer) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c5b66bff-6dbb-43c0-bffa-317133ca5b9e
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 0b9660433b357d6ec1ddead86611387e0cb5c11a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-change-the-return-type-of-a-datacontext-method-or-designer"></a>Cómo: cambiar el tipo de valor devuelto de un método de DataContext (Object Relational Designer)
El tipo de valor devuelto de un método de <xref:System.Data.Linq.DataContext> (creado a partir de un procedimiento almacenado o una función) difiere según la ubicación donde se coloque el procedimiento almacenado o la función en el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Si se coloca un elemento directamente en una clase de entidad existente, se crea un método de <xref:System.Data.Linq.DataContext> que tiene el tipo de valor devuelto de la clase de entidad (si el esquema de los datos devueltos por el procedimiento almacenado o la función coincide con la forma de la clase de entidad). Si se coloca un elemento en un área vacía del [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], se crea un método de <xref:System.Data.Linq.DataContext> que devuelve un tipo generado automáticamente. Se puede cambiar el tipo de valor devuelto de un método de <xref:System.Data.Linq.DataContext> después de agregarlo al panel de métodos. Para examinar o cambiar el tipo de valor devuelto de un <xref:System.Data.Linq.DataContext> método, selecciónelo y haga clic en el **tipo de valor devuelto** propiedad en el **propiedades** ventana.  
  
> [!NOTE]
>  No se puede revertir <xref:System.Data.Linq.DataContext> métodos que tienen un tipo de valor devuelto establecido en una clase de entidad para devolver el tipo generado automáticamente mediante el uso de la **propiedades** ventana. Para revertir un método de <xref:System.Data.Linq.DataContext> de modo que devuelva un tipo generado automáticamente, debe arrastrar de nuevo el objeto de base de datos original hasta Object Relational Designer.  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="to-change-the-return-type-of-a-datacontext-method-from-the-auto-generated-type-to-an-entity-class"></a>Para cambiar el tipo de valor devuelto de un método de DataContext del tipo generado automáticamente a una clase de entidad  
  
1.  Seleccione el método de <xref:System.Data.Linq.DataContext> en el panel de métodos.  
  
2.  Seleccione **tipo de valor devuelto** en el **propiedades** clase de ventana y, a continuación, seleccione una entidad disponible en la **tipo de valor devuelto** lista. Si la clase de entidad que desea no está en la lista, agréguela a o créela en el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] para agregarlo a la lista.  
  
3.  Guarde el archivo .dbml.  
  
## <a name="to-change-the-return-type-of-a-datacontext-method-from-an-entity-class-back-to-the-auto-generated-type"></a>Para volver a cambiar el tipo de valor devuelto de un método de DataContext de una clase de entidad al tipo generado automáticamente  
  
1.  Seleccione el método de <xref:System.Data.Linq.DataContext> en el panel de métodos y elimínelo.  
  
2.  Arrastre el objeto de base de datos desde **Explorador de servidores**/**el Explorador de base de datos** en un área vacía de Object Relational Designer.  
  
3.  Guarde el archivo .dbml.  
  
## <a name="see-also"></a>Vea también
[LINQ to SQL herramientas en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
[LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)   
[Métodos de DataContext (Object Relational Designer)](../data-tools/datacontext-methods-o-r-designer.md)   
[Cómo: crear métodos DataContext asignados a procedimientos almacenados y funciones (Object Relational Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)