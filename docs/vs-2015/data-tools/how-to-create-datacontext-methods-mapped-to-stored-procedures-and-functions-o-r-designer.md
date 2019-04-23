---
title: Procedimiento Crear métodos DataContext asignados a procedimientos almacenados y funciones (Object Relational Designer) | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: e7ca32f1-50b3-48af-ad92-ceafd749296a
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8485885cbba43ea9eaef76616607861c44c2ab24
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/17/2019
ms.locfileid: "59668787"
---
# <a name="how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-or-designer"></a>Procedimiento Crear métodos DataContext asignados a funciones y procedimientos almacenados (Object Relational Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Procedimientos almacenados y funciones se pueden agregar a la [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] como <xref:System.Data.Linq.DataContext> métodos. Al llamar al método y pasar los parámetros necesarios se ejecuta el procedimiento almacenado o la función en la base de datos y se devuelven los datos en el tipo de valor devuelto del método <xref:System.Data.Linq.DataContext>. Para obtener información detallada sobre <xref:System.Data.Linq.DataContext> métodos, vea [métodos DataContext (Object Relational Designer)](../data-tools/datacontext-methods-o-r-designer.md).  
  
> [!NOTE]
>  Los procedimientos almacenados también se pueden usar para invalidar el comportamiento predeterminado de [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] en tiempo de ejecución para las inserciones, actualizaciones y eliminaciones cuando se guardan los cambios de las clases de entidad en una base de datos. Para obtener más información, vea [Cómo: Asignación de procedimientos almacenados para realizar actualizaciones, inserciones y eliminaciones (Object Relational Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).  
  
## <a name="creating-datacontext-methods"></a>Crear métodos de DataContext  
 Puede crear <xref:System.Data.Linq.DataContext> métodos arrastrando procedimientos almacenan o funciones desde **Server Explorer/Database Explorer** hasta el [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
> [!NOTE]
>  El tipo de valor devuelto del método de <xref:System.Data.Linq.DataContext> generado difiere según la ubicación donde se coloque el procedimiento almacenado o la función en el [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Si se coloca un elemento directamente en una clase de entidad existente, se crea un método de <xref:System.Data.Linq.DataContext> con el tipo de valor devuelto de la clase de entidad. Si se coloca un elemento en un área vacía del [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], se crea un método de <xref:System.Data.Linq.DataContext> que devuelve un tipo generado automáticamente. Puede cambiar el tipo de valor devuelto de un <xref:System.Data.Linq.DataContext> método después de agregarlo al panel de métodos. Para examinar o cambiar el tipo de valor devuelto de un método <xref:System.Data.Linq.DataContext>, selecciónelo y fíjese en la propiedad **Tipo devuelto** en la ventana **Propiedades**. Para obtener más información, vea [Cómo: Cambio del tipo de valor devuelto de un método DataContext (Object Relational Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-create-datacontext-methods-that-return-automatically-generated-types"></a>Para crear métodos de DataContext que devuelvan tipos generados automáticamente  
  
1.  En **Explorador de servidores**/**Database Explorer**, expanda el **Stored Procedures** nodo de la base de datos que está trabajando.  
  
2.  Busque el procedimiento almacenado que desee y arrástrelo hasta un área vacía del [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
     El método <xref:System.Data.Linq.DataContext> se crea con un tipo de valor devuelto generado automáticamente y aparece en el panel **Métodos**.  
  
#### <a name="to-create-datacontext-methods-that-have-the-return-type-of-an-entity-class"></a>Para crear métodos de DataContext con el tipo de valor devuelto de una clase de entidad  
  
1.  En **Explorador de servidores**/**Database Explorer**, expanda el **Stored Procedures** nodo de la base de datos que está trabajando.  
  
2.  Busque el procedimiento almacenado que desee y arrástrelo hasta una clase de entidad existente en el [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
     El método <xref:System.Data.Linq.DataContext> se crea con el tipo de valor devuelto de la clase de entidad seleccionada y aparece en el panel **Métodos**.  
  
> [!NOTE]
>  Para obtener información acerca de cómo cambiar el tipo de valor devuelto de existente <xref:System.Data.Linq.DataContext> métodos, vea [Cómo: Cambio del tipo de valor devuelto de un método DataContext (Object Relational Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).  
  
## <a name="see-also"></a>Vea también  
 [LINQ to SQL Tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Métodos DataContext (Object Relational Designer)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Tutorial: Crear clases LINQ to SQL (Object Relational Designer)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Introducción a LINQ en Visual Basic](http://msdn.microsoft.com/library/3047d86e-0d49-40e2-928b-dc02e46c7984)   
 [Cómo: Escribir consultas LINQ en C#](http://msdn.microsoft.com/library/45e47fcc-cfa1-4b72-b161-d038ae87bd23)
