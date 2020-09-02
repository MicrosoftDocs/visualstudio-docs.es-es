---
title: 'Cómo: crear métodos DataContext asignados a funciones y procedimientos almacenados (Object Relational Designer) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: e7ca32f1-50b3-48af-ad92-ceafd749296a
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 70053b74a4dd2ad569e1e8195f4c9b2e7b214440
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665972"
---
# <a name="how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-or-designer"></a>Procedimiento para crear métodos DataContext asignados a funciones y procedimientos almacenados (Object Relational Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los procedimientos almacenados y las funciones se pueden agregar a los [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] <xref:System.Data.Linq.DataContext> métodos as. Al llamar al método y pasar los parámetros necesarios se ejecuta el procedimiento almacenado o la función en la base de datos y se devuelven los datos en el tipo de valor devuelto del método <xref:System.Data.Linq.DataContext>. Para obtener información detallada sobre <xref:System.Data.Linq.DataContext> los métodos, vea [método DataContext (Object](../data-tools/datacontext-methods-o-r-designer.md)Relational Designer).

> [!NOTE]
> Los procedimientos almacenados también se pueden usar para invalidar el comportamiento predeterminado de [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] en tiempo de ejecución para las inserciones, actualizaciones y eliminaciones cuando se guardan los cambios de las clases de entidad en una base de datos. Para obtener más información, vea [Cómo: asignar procedimientos almacenados para realizar actualizaciones, inserciones y eliminaciones (Object](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)Relational Designer).

## <a name="creating-datacontext-methods"></a>Crear métodos de DataContext
 Puede crear <xref:System.Data.Linq.DataContext> métodos arrastrando procedimientos almacenados o funciones desde **Explorador de servidores/Explorador de bases de datos** hasta el [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] .

> [!NOTE]
> El tipo de valor devuelto del método de <xref:System.Data.Linq.DataContext> generado difiere según la ubicación donde se coloque el procedimiento almacenado o la función en el [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Si se coloca un elemento directamente en una clase de entidad existente, se crea un método de <xref:System.Data.Linq.DataContext> con el tipo de valor devuelto de la clase de entidad. Si se coloca un elemento en un área vacía del [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], se crea un método de <xref:System.Data.Linq.DataContext> que devuelve un tipo generado automáticamente. Puede cambiar el tipo de valor devuelto de un <xref:System.Data.Linq.DataContext> método después de agregarlo al panel de métodos. Para examinar o cambiar el tipo de valor devuelto de un método <xref:System.Data.Linq.DataContext>, selecciónelo y fíjese en la propiedad **Tipo devuelto** en la ventana **Propiedades**. Para obtener más información, vea [Cómo: cambiar el tipo de valor devuelto de un método DataContext (Object](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)Relational Designer).

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-create-datacontext-methods-that-return-automatically-generated-types"></a>Para crear métodos de DataContext que devuelvan tipos generados automáticamente

1. En **Explorador de servidores** / **Explorador de bases de datos**, expanda el nodo **procedimientos almacenados** de la base de datos con la que está trabajando.

2. Busque el procedimiento almacenado que desee y arrástrelo hasta un área vacía del [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

     El método <xref:System.Data.Linq.DataContext> se crea con un tipo de valor devuelto generado automáticamente y aparece en el panel **Métodos**.

#### <a name="to-create-datacontext-methods-that-have-the-return-type-of-an-entity-class"></a>Para crear métodos de DataContext con el tipo de valor devuelto de una clase de entidad

1. En **Explorador de servidores** / **Explorador de bases de datos**, expanda el nodo **procedimientos almacenados** de la base de datos con la que está trabajando.

2. Busque el procedimiento almacenado que desee y arrástrelo hasta una clase de entidad existente en el [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

     El método <xref:System.Data.Linq.DataContext> se crea con el tipo de valor devuelto de la clase de entidad seleccionada y aparece en el panel **Métodos**.

> [!NOTE]
> Para obtener información acerca de cómo cambiar el tipo de valor devuelto de existente <xref:System.Data.Linq.DataContext> métodos, vea [Cómo: Cambiar el tipo de valor devuelto de un método DataContext (Object Relational Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

## <a name="see-also"></a>Consulte también
 [LINQ to SQL herramientas en](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [los métodos DataContext](../data-tools/datacontext-methods-o-r-designer.md) de Visual Studio (Object Relational Designer) [Tutorial: crear clases LINQ to SQL (object relational Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [Introducción a LINQ en Visual Basic](https://msdn.microsoft.com/library/3047d86e-0d49-40e2-928b-dc02e46c7984) [Cómo: escribir consultas LINQ en C#](https://msdn.microsoft.com/library/45e47fcc-cfa1-4b72-b161-d038ae87bd23)
