---
title: 'Cómo: crear consultas de TableAdapter | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- TableAdapters, creating queries
- queries [Visual Studio], creating
- data [Visual Studio], TableAdapter queries
- queries [Visual Studio], TableAdapters
ms.assetid: df0cf4a5-e9cc-4de6-8b94-ce74fb7b2452
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: f7d4bd84d5cd4538d06048fd6953fa95fc344da0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47577365"
---
# <a name="how-to-create-tableadapter-queries"></a>Cómo: Crear consultas de TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Las consultas de TableAdapter son instrucciones SQL o procedimientos almacenados que se puede ejecutar la aplicación en una base de datos.  
  
 Agregue tantas consultas a un TableAdapter como requiera la aplicación. Las consultas de TableAdapter aparecen como métodos en un TableAdapter. Cuando se crea una consulta denominada `FillByCity` que toma un parámetro que representa el valor de la ciudad, la consulta se agrega al objeto TableAdapter. Se agrega como un método con tipo que toma el tipo de parámetro como un argumento correcto, en este caso, una cadena que representa el valor de la ciudad. Llamar a la consulta de TableAdapter al igual que cualquier método en cualquier objeto. Por ejemplo, el código siguiente ejecuta la `FillByCity` consulta y rellena el `Customers` tabla con todos los clientes con un valor de la ciudad de `Seattle`:  
  
 [!code-csharp[VbRaddataTableAdapters#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/Form1.cs#1)]
 [!code-vb[VbRaddataTableAdapters#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/Form1.vb#1)]  
  
 Consultas de TableAdapter pueden rellenar una tabla de datos (`Fill` y `FillBy` consultas) o devolver nuevas tablas de datos que se rellena con los datos devueltos por la consulta (`GetData` y `GetDataBy` consultas).  
  
 Puede agregar consultas a los TableAdapters existentes mediante la ejecución de la [editar TableAdapters](../data-tools/editing-tableadapters.md). (Haga clic en cualquier TableAdapter y elija **Add Query**.)  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="create-a-query-in-the-dataset-designer"></a>Crear una consulta en el Diseñador de Dataset  
  
#### <a name="to-add-a-query-to-a-tableadapter-in-the-dataset-designer"></a>Para agregar una consulta a un TableAdapter en el Diseñador de Dataset  
  
1.  Abrir un conjunto de datos en el **Diseñador de Dataset**. Para obtener más información, consulte [Cómo: abrir un conjunto de datos en el Diseñador de Dataset](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Haga clic en el TableAdapter deseado y seleccione **Agregar consulta**.  
  
     O bien  
  
3.  Arrastre un **consulta** desde el **conjunto de datos** pestaña de la **cuadro de herramientas** en una tabla en el diseñador.  
  
     El **TableAdapter Query Configuration Wizard** se abre.  
  
4.  Complete el Asistente; la consulta se agrega al objeto TableAdapter.  
  
## <a name="create-a-query-directly-on-a-form-in-your-windows-application"></a>Crear una consulta directamente en un formulario de la aplicación de Windows  
 Si tiene una instancia de un TableAdapter en el formulario puede agregar una consulta mediante el [cuadro de diálogo de generador de criterios de búsqueda](http://msdn.microsoft.com/library/0b306b92-f35e-45ef-a4be-3f653cd00c3d), que agrega un <xref:System.Windows.Forms.ToolStrip> control al formulario que acepte cualquier entrada parámetros requeridos por la consulta, así como un botón para ejecutar la consulta.  
  
#### <a name="to-add-a-query-to-a-tableadapter-using-the-search-criteria-dialog-box"></a>Para agregar una consulta a un TableAdapter utilizando el cuadro de diálogo criterios de búsqueda  
  
1.  Seleccione un TableAdapter en la Bandeja de componentes.  
  
2.  Haga clic en la etiqueta inteligente del TableAdapter y elija **Agregar consulta**.  
  
3.  Complete el cuadro de diálogo y la consulta se agrega al objeto TableAdapter. Para obtener más información, consulte [cuadro de diálogo de generador de criterios de búsqueda](http://msdn.microsoft.com/library/0b306b92-f35e-45ef-a4be-3f653cd00c3d).  
  
## <a name="see-also"></a>Vea también  
 [Información general sobre TableAdapter](../data-tools/tableadapter-overview.md)   
 [Cómo: editar consultas de TableAdapter](../data-tools/how-to-edit-tableadapter-queries.md)   
 [Crear y editar conjuntos de datos con tipo](../data-tools/creating-and-editing-typed-datasets.md)   
 [Agregar nuevos orígenes de datos](../data-tools/add-new-data-sources.md)   
 [Cómo: Conectarse a los datos de una base de datos](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Validación de datos](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Cómo: desplazarse por datos con el Control BindingNavigator de formularios de Windows](http://msdn.microsoft.com/library/0e5d4f34-bc9b-47cf-9b8d-93acbb1f1dbb)   
 [Tutorial: Mostrar datos en un formulario de Windows](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [Tutorial: Crear un objeto TableAdapter con varias consultas](../data-tools/walkthrough-creating-a-tableadapter-with-multiple-queries.md)