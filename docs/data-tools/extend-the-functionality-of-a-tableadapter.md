---
title: Ampliar la funcionalidad de un TableAdapter
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 34a5c1601071a36ca11005503e2f443a72ca3dfe
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586645"
---
# <a name="extend-the-functionality-of-a-tableadapter"></a>Ampliar la funcionalidad de un TableAdapter

Puede extender la funcionalidad de un TableAdapter agregando código al archivo de clase parcial del TableAdapter.

El código que define un TableAdapter se vuelve a generar cuando se realizan cambios en el TableAdapter en el **Diseñador de DataSet**, o cuando un asistente modifica la configuración de un TableAdapter. Para evitar que se elimine el código durante la regeneración de un TableAdapter, agregue código al archivo de clase parcial del TableAdapter.

Las clases parciales permiten que el código de una clase específica se divida entre varios archivos físicos. Para obtener más información, vea [partial](/dotnet/visual-basic/language-reference/modifiers/partial) o [partial (Type)](/dotnet/csharp/language-reference/keywords/partial-type).

## <a name="locate-tableadapters-in-code"></a>Buscar TableAdapters en el código

Aunque los TableAdapters están diseñados con el **Diseñador de DataSet**, las clases de TableAdapter que se generan no son clases anidadas de <xref:System.Data.DataSet>. Los TableAdapters se encuentran en un espacio de nombres basado en el nombre del conjunto de objetos asociado del TableAdapter. Por ejemplo, si la aplicación contiene un conjunto de objetos denominado `HRDataSet`, los TableAdapters se encontrarían en el espacio de nombres `HRDataSetTableAdapters`. (La convención de nomenclatura sigue este patrón: *DatasetName* + `TableAdapters`).

En el ejemplo siguiente se supone que un TableAdapter denominado `CustomersTableAdapter`está en un proyecto con `NorthwindDataSet`.

### <a name="to-create-a-partial-class-for-a-tableadapter"></a>Para crear una clase parcial para un TableAdapter

1. Agregue una nueva clase al proyecto; para ello, vaya al menú **proyecto** y seleccione **Agregar clase**.

2. Asigne a la clase el nombre `CustomersTableAdapterExtended`.

3. Seleccione **Agregar**.

4. Reemplace el código por el espacio de nombres correcto y el nombre de clase parcial del proyecto como se indica a continuación:

     [!code-csharp[VbRaddataTableAdapters#2](../data-tools/codesnippet/CSharp/extend-the-functionality-of-a-tableadapter_1.cs)]
     [!code-vb[VbRaddataTableAdapters#2](../data-tools/codesnippet/VisualBasic/extend-the-functionality-of-a-tableadapter_1.vb)]

## <a name="see-also"></a>Vea también

- [Llenar conjuntos de datos mediante TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)
