---
title: Ampliar la funcionalidad de un TableAdapter
description: Aprenda a ampliar la funcionalidad de un TableAdapter agregando código al archivo de clase parcial del TableAdapter.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 6e1c594ab1f74cddb962cc2a6d4030ede1e53c8f
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/10/2020
ms.locfileid: "94435083"
---
# <a name="extend-the-functionality-of-a-tableadapter"></a>Ampliar la funcionalidad de un TableAdapter

Puede extender la funcionalidad de un TableAdapter agregando código al archivo de clase parcial del TableAdapter.

El código que define un TableAdapter se vuelve a generar cuando se realizan cambios en el TableAdapter en el **Diseñador de DataSet** , o cuando un asistente modifica la configuración de un TableAdapter. Para evitar que se elimine el código durante la regeneración de un TableAdapter, agregue código al archivo de clase parcial del TableAdapter.

Las clases parciales permiten que el código de una clase específica se divida entre varios archivos físicos. Para obtener más información, vea [partial](/dotnet/visual-basic/language-reference/modifiers/partial) o [partial (Type)](/dotnet/csharp/language-reference/keywords/partial-type).

## <a name="locate-tableadapters-in-code"></a>Buscar TableAdapters en el código

Aunque los TableAdapters están diseñados con el **Diseñador de DataSet** , las clases de TableAdapter que se generan no son clases anidadas de <xref:System.Data.DataSet> . Los TableAdapters se encuentran en un espacio de nombres basado en el nombre del conjunto de objetos asociado del TableAdapter. Por ejemplo, si la aplicación contiene un conjunto de `HRDataSet` objetos denominado, los TableAdapters se ubicarían en el `HRDataSetTableAdapters` espacio de nombres. (La Convención de nomenclatura sigue este patrón: *DatasetName*  +  `TableAdapters` ).

En el ejemplo siguiente se supone que un TableAdapter denominado `CustomersTableAdapter` está en un proyecto con `NorthwindDataSet` .

### <a name="to-create-a-partial-class-for-a-tableadapter"></a>Para crear una clase parcial para un TableAdapter

1. Agregue una nueva clase al proyecto; para ello, vaya al menú **proyecto** y seleccione **Agregar clase**.

2. Asigne `CustomersTableAdapterExtended` como nombre de la clase.

3. Seleccione **Agregar**.

4. Reemplace el código por el espacio de nombres correcto y el nombre de clase parcial del proyecto como se indica a continuación:

     [!code-csharp[VbRaddataTableAdapters#2](../data-tools/codesnippet/CSharp/extend-the-functionality-of-a-tableadapter_1.cs)]
     [!code-vb[VbRaddataTableAdapters#2](../data-tools/codesnippet/VisualBasic/extend-the-functionality-of-a-tableadapter_1.vb)]

## <a name="see-also"></a>Consulte también

- [Rellenar conjuntos de datos mediante TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)
