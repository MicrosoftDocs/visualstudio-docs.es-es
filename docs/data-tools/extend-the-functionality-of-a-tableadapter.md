---
title: Ampliar la funcionalidad de un TableAdapter | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], TableAdapters
- data [Visual Studio], extending TableAdapters
- TableAdapters, adding functionality
ms.assetid: 418249c8-c7f3-47ef-a94c-744cb6fe6aaf
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: d163461f559432752815d2f1e1fec103d93a84ec
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="extend-the-functionality-of-a-tableadapter"></a>Ampliar la funcionalidad de un TableAdapter
Puede ampliar la funcionalidad de un TableAdapter agregando código al archivo de clase parcial del TableAdapter.  
  
 El código que define un objeto TableAdapter se vuelve a generar cuando se realizan cambios en el TableAdapter en el **Diseñador de Dataset**, o cuando un asistente modifica la configuración de un TableAdapter. Para evitar que el código que se eliminen durante la regeneración de un TableAdapter, agregue código al archivo de clase parcial del TableAdapter.  
  
 Clases parciales permiten código para una clase concreta se divida entre varios archivos físicos. Para obtener más información, consulte [parcial](/dotnet/visual-basic/language-reference/modifiers/partial) o [partial (tipos)](/dotnet/csharp/language-reference/keywords/partial-type).  
  
## <a name="locate-tableadapters-in-code"></a>Busque los TableAdapters en el código  
 Aunque los objetos TableAdapter se diseñan con el **Diseñador de Dataset**, las clases TableAdapter generadas no son clases anidadas de <xref:System.Data.DataSet>. Los TableAdapters se encuentran en un espacio de nombres basado en el nombre del conjunto de datos asociado del TableAdapter. Por ejemplo, si la aplicación contiene un conjunto de datos denominado `HRDataSet`, los TableAdapters debería encontrarse en la `HRDataSetTableAdapters` espacio de nombres. (La convención de nomenclatura sigue este patrón: *DatasetName* + `TableAdapters`).  
  
 El ejemplo siguiente supone un TableAdapter denominado `CustomersTableAdapter`está en un proyecto con `NorthwindDataSet`.  
  
#### <a name="to-create-a-partial-class-for-a-tableadapter"></a>Para crear una clase parcial para un TableAdapter  
  
1.  Agregue una nueva clase al proyecto, vaya a la **proyecto** menú y seleccionando **Agregar clase**.  
  
2.  Asigne a la clase el nombre `CustomersTableAdapterExtended`.  
  
3.  Seleccione **agregar**.  
  
4.  Reemplace el código con el espacio de nombres correcto y el nombre de clase parcial para el proyecto como se indica a continuación:  
  
     [!code-csharp[VbRaddataTableAdapters#2](../data-tools/codesnippet/CSharp/extend-the-functionality-of-a-tableadapter_1.cs)]
     [!code-vb[VbRaddataTableAdapters#2](../data-tools/codesnippet/VisualBasic/extend-the-functionality-of-a-tableadapter_1.vb)]  
  
## <a name="see-also"></a>Vea también  
 [Llenar conjuntos de datos mediante TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)