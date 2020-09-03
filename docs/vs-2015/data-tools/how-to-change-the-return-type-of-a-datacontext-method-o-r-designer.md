---
title: 'Cómo: cambiar el tipo de valor devuelto de un método DataContext (Object Relational Designer) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: c5b66bff-6dbb-43c0-bffa-317133ca5b9e
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 351a2f53d8ad8c5f29821d905c292cd988390869
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658837"
---
# <a name="how-to-change-the-return-type-of-a-datacontext-method-or-designer"></a>Procedimiento para cambiar el tipo de valor devuelto de un método DataContext (Object Relational Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El tipo de valor devuelto de un método de <xref:System.Data.Linq.DataContext> (creado a partir de un procedimiento almacenado o una función) difiere según la ubicación donde se coloque el procedimiento almacenado o la función en el [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Si se coloca un elemento directamente en una clase de entidad existente, se crea un método de <xref:System.Data.Linq.DataContext> que tiene el tipo de valor devuelto de la clase de entidad (si el esquema de los datos devueltos por el procedimiento almacenado o la función coincide con la forma de la clase de entidad). Si se coloca un elemento en un área vacía del [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], se crea un método de <xref:System.Data.Linq.DataContext> que devuelve un tipo generado automáticamente. Se puede cambiar el tipo de valor devuelto de un método de <xref:System.Data.Linq.DataContext> después de agregarlo al panel de métodos. Para examinar o cambiar el tipo de valor devuelto de un método <xref:System.Data.Linq.DataContext>, selecciónelo y haga clic en la propiedad **Tipo devuelto** en la ventana **Propiedades**.

> [!NOTE]
> Mediante la ventana **Propiedades**, no se pueden revertir los métodos de <xref:System.Data.Linq.DataContext> cuyo tipo de valor devuelto está establecido en una clase de entidad para que devuelvan el tipo generado automáticamente. Para revertir un método de <xref:System.Data.Linq.DataContext> de modo que devuelva un tipo generado automáticamente, debe arrastrar de nuevo el objeto de base de datos original hasta Object Relational Designer.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

### <a name="to-change-the-return-type-of-a-datacontext-method-from-the-auto-generated-type-to-an-entity-class"></a>Para cambiar el tipo de valor devuelto de un método de DataContext del tipo generado automáticamente a una clase de entidad

1. Seleccione el método de <xref:System.Data.Linq.DataContext> en el panel de métodos.

2. Seleccione **Tipo devuelto** en la ventana **Propiedades** y después seleccione una clase de entidad disponible en la lista **Tipo devuelto**. Si la clase de entidad deseada no está en la lista, agréguela a o créela en el [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] para agregarla a la lista.

3. Guarde el archivo .dbml.

### <a name="to-change-the-return-type-of-a-datacontext-method-from-an-entity-class-back-to-the-auto-generated-type"></a>Para volver a cambiar el tipo de valor devuelto de un método de DataContext de una clase de entidad al tipo generado automáticamente

1. Seleccione el método de <xref:System.Data.Linq.DataContext> en el panel de métodos y elimínelo.

2. Arrastre el objeto de base de datos de **Explorador de servidores** / **Explorador de bases de datos** a un área vacía de Object Relational Designer.

3. Guarde el archivo .dbml.

## <a name="see-also"></a>Consulte también
 [Herramientas de LINQ to SQL en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [métodos DataContext (Object Relational Designer)](../data-tools/datacontext-methods-o-r-designer.md) [Cómo: crear métodos de DataContext asignados a funciones y procedimientos almacenados (Object](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md) Relational Designer)
