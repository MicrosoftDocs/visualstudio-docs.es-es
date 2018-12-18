---
title: 'Cómo: cambiar el tipo de valor devuelto de un método DataContext (Object Relational Designer) | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c5b66bff-6dbb-43c0-bffa-317133ca5b9e
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e4999c9fd273b78ff740e53c25bbe5a4b0a3017f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49211749"
---
# <a name="how-to-change-the-return-type-of-a-datacontext-method-or-designer"></a>Cómo: cambiar el tipo de valor devuelto de un método DataContext (Object Relational Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
El tipo de valor devuelto de un método de <xref:System.Data.Linq.DataContext> (creado a partir de un procedimiento almacenado o una función) difiere según la ubicación donde se coloque el procedimiento almacenado o la función en el [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Si se coloca un elemento directamente en una clase de entidad existente, se crea un método de <xref:System.Data.Linq.DataContext> que tiene el tipo de valor devuelto de la clase de entidad (si el esquema de los datos devueltos por el procedimiento almacenado o la función coincide con la forma de la clase de entidad). Si se coloca un elemento en un área vacía del [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], se crea un método de <xref:System.Data.Linq.DataContext> que devuelve un tipo generado automáticamente. Se puede cambiar el tipo de valor devuelto de un método de <xref:System.Data.Linq.DataContext> después de agregarlo al panel de métodos. Para examinar o cambiar el tipo de valor devuelto de un <xref:System.Data.Linq.DataContext> método, selecciónelo y haga clic en el **Return Type** propiedad en el **propiedades** ventana.  
  
> [!NOTE]
>  No se puede revertir <xref:System.Data.Linq.DataContext> los métodos que tienen un tipo de valor devuelto se establece en una clase de entidad para devolver el tipo generado automáticamente mediante el **propiedades** ventana. Para revertir un método de <xref:System.Data.Linq.DataContext> de modo que devuelva un tipo generado automáticamente, debe arrastrar de nuevo el objeto de base de datos original hasta Object Relational Designer.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-change-the-return-type-of-a-datacontext-method-from-the-auto-generated-type-to-an-entity-class"></a>Para cambiar el tipo de valor devuelto de un método de DataContext del tipo generado automáticamente a una clase de entidad  
  
1.  Seleccione el método de <xref:System.Data.Linq.DataContext> en el panel de métodos.  
  
2.  Seleccione **Return Type** en el **propiedades** clase de ventana y, a continuación, seleccione una entidad disponible en el **Return Type** lista. Si la clase de entidad deseada no está en la lista, agréguelo a o créela en el [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] para agregarlo a la lista.  
  
3.  Guarde el archivo .dbml.  
  
### <a name="to-change-the-return-type-of-a-datacontext-method-from-an-entity-class-back-to-the-auto-generated-type"></a>Para volver a cambiar el tipo de valor devuelto de un método de DataContext de una clase de entidad al tipo generado automáticamente  
  
1.  Seleccione el método de <xref:System.Data.Linq.DataContext> en el panel de métodos y elimínelo.  
  
2.  Arrastre el objeto de base de datos desde **Explorador de servidores**/**Database Explorer** en un área vacía de Object Relational Designer.  
  
3.  Guarde el archivo .dbml.  
  
## <a name="see-also"></a>Vea también  
 [LINQ to SQL Tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Métodos DataContext (Object Relational Designer)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Cómo: Crear métodos DataContext asignados a funciones y procedimientos almacenados (Object Relational Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)

