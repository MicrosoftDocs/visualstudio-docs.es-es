---
title: Métodos de DataContext (Object Relational Designer) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: c149f4e5-3b61-4c33-892e-3e26d47f3eeb
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 05acf62d30a1ac272003c0883b4a8c927e13e659
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58997917"
---
# <a name="datacontext-methods-or-designer"></a>DataContext (Métodos) (Object Relational Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
DataContext] (assetId:///T:System.Data.Linq.DataContext?qualifyHint=False & autoUpgrade = True) métodos (en el contexto de la [LINQ to SQL Tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)) son métodos de la <xref:System.Data.Linq.DataContext> clase que se ejecutan almacenado procedimientos y funciones en una base de datos.  
  
 La clase <xref:System.Data.Linq.DataContext> es una clase de [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] que actúa como una vía entre una base de datos de SQL Server y las clases de entidad de [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] asignadas a esa base de datos. La clase <xref:System.Data.Linq.DataContext> contiene la información de la cadena de conexión y los métodos para realizar la conexión a una base de datos y manipular los datos de la base de datos. De forma predeterminada, la clase <xref:System.Data.Linq.DataContext> contiene varios métodos a los que se puede llamar, como el método <xref:System.Data.Linq.DataContext.SubmitChanges%2A> que envía los datos actualizados de las clases de [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] a la base de datos. También se pueden crear métodos <xref:System.Data.Linq.DataContext> adicionales que se asignan a los procedimientos almacenados y funciones. Es decir, al llamar a estos métodos personalizados, se ejecutará el procedimiento almacenado o la función en la base de datos a la que está asignado el método de <xref:System.Data.Linq.DataContext>. Se pueden agregar métodos nuevos a la clase <xref:System.Data.Linq.DataContext> de la misma forma que se agregarían métodos para extender cualquier clase. Sin embargo, en las discusiones sobre <xref:System.Data.Linq.DataContext> métodos en el contexto de la [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], es el <xref:System.Data.Linq.DataContext> métodos que se asignan a los procedimientos almacenados y funciones que se analizan.  
  
## <a name="methods-pane"></a>Panel de métodos  
 Los métodos de <xref:System.Data.Linq.DataContext> que se asignan a los procedimientos almacenados y funciones se muestran en el panel de métodos del [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. El panel de métodos es el panel en el lado de la **entidades** panel (la superficie de diseño principal). Muestra el panel de métodos todos <xref:System.Data.Linq.DataContext> métodos que ha creado mediante el [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. De forma predeterminada, el panel de métodos está vacío; Arrastre los procedimientos almacenados o funciones desde **Explorador de servidores**/**Database Explorer** hasta la [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] para crear <xref:System.Data.Linq.DataContext> métodos y rellenar el panel de métodos. Para obtener más información, vea [Cómo: Crear métodos DataContext asignados a funciones y procedimientos almacenados (Object Relational Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md).  
  
> [!NOTE]
>  Abrir y cerrar el panel de métodos haciendo clic con el [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] y, a continuación, haga clic en **ocultar panel métodos** o **Mostrar panel métodos**, o utilice el método abreviado de teclado CTRL + 1.  
  
## <a name="two-types-of-datacontext-methods"></a>Dos tipos de métodos de DataContext  
 Los métodos de DataContext son los que se asignan a los procedimientos almacenados y funciones de la base de datos. Puede crear y agregar métodos DataContext en el panel de métodos de [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Hay dos tipos distintos de métodos <xref:System.Data.Linq.DataContext>; los que devuelven uno o varios conjuntos de resultados y los que no:  
  
-   Métodos de <xref:System.Data.Linq.DataContext> que devuelven uno o varios conjuntos de resultados:  
  
     Cree este tipo de método de <xref:System.Data.Linq.DataContext> cuando la aplicación solamente necesite ejecutar los procedimientos almacenados y funciones en la base de datos y devolver los resultados. Para obtener más información, vea [Cómo: Crear métodos DataContext asignados a procedimientos almacenados y funciones (Object Relational Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md), System.Data.Linq.ISingleResult\<T >, y <xref:System.Data.Linq.IMultipleResults>.  
  
-   Métodos de <xref:System.Data.Linq.DataContext> que no devuelven conjuntos de resultados, como Inserts, Updates y Deletes para una clase de entidad concreta.  
  
     Cree este tipo de método de <xref:System.Data.Linq.DataContext> cuando la aplicación tenga que ejecutar los procedimientos almacenados en lugar de usar el comportamiento predeterminado de [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] para guardar los datos modificados entre una clase de entidad y la base de datos. Para obtener más información, vea [Cómo: Asignación de procedimientos almacenados para realizar actualizaciones, inserciones y eliminaciones (Object Relational Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).  
  
## <a name="return-types-of-datacontext-methods"></a>Tipos de valor devuelto de los métodos de DataContext  
 Cuando arrastre los procedimientos almacenados y funciones de **Explorador de servidores**/**Database Explorer** hasta la [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], el tipo de valor devuelto de generado <xref:System.Data.Linq.DataContext> difiere del método Dependiendo de dónde colocar el elemento. Al colocar los elementos directamente en una clase de entidad existentes, crea un <xref:System.Data.Linq.DataContext> método con el tipo de valor devuelto de la clase de entidad; al colocar los elementos en un área vacía de la [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] (en cualquiera de los paneles) crea un <xref:System.Data.Linq.DataContext> método que devuelva una tipo generado automáticamente. El tipo generado automáticamente coincide con el nombre del procedimiento almacenado o de la función y sus propiedades se asignan a los campos devueltos por el procedimiento almacenado o la función.  
  
> [!NOTE]
>  Se puede cambiar el tipo de valor devuelto de un método de <xref:System.Data.Linq.DataContext> después de agregarlo al panel de métodos. Para examinar o cambiar el tipo de valor devuelto de un método <xref:System.Data.Linq.DataContext>, selecciónelo y fíjese en la propiedad **Tipo devuelto** en la ventana **Propiedades**. Para obtener más información, vea [Cómo: Cambio del tipo de valor devuelto de un método DataContext (Object Relational Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).  
  
 Los objetos que se arrastran desde la base de datos a la superficie de Object Relational Designer reciben automáticamente un nombre basado en el nombre de los objetos de la base de datos. Si arrastra el mismo objeto más de una vez, se anexa un número al final del nuevo nombre para diferenciar los nombres. Cuando los nombres de objetos de la base de datos contienen espacios o caracteres no admitidos en Visual Basic o C#, el espacio o el carácter no válido se sustituye por un carácter de subrayado.  
  
## <a name="see-also"></a>Vea también  
 [LINQ to SQL Tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Procedimientos almacenados](http://msdn.microsoft.com/library/4d23dd7a-a85f-44ff-a717-af7d0950c0fc)   
 [Cómo: Crear métodos DataContext asignados a procedimientos almacenados y funciones (Object Relational Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)   
 [Cómo: Asignar procedimientos almacenados para realizar actualizaciones, inserciones y eliminaciones (Object Relational Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [Tutorial: Personalización de la inserción, actualización y eliminación de comportamiento de las clases de entidad](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)   
 [Tutorial: Crear clases LINQ to SQL (Object Relational Designer)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)
