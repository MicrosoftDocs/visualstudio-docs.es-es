---
title: Extender la funcionalidad de un TableAdapter | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], TableAdapters
- data [Visual Studio], extending TableAdapters
- TableAdapters, adding functionality
ms.assetid: 418249c8-c7f3-47ef-a94c-744cb6fe6aaf
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 19367f812a87d6aa585e123100f1d08144c57ff9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672357"
---
# <a name="extend-the-functionality-of-a-tableadapter"></a>Ampliar la funcionalidad de un TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede extender la funcionalidad de un TableAdapter agregando código al archivo de clase parcial del TableAdapter.

 El código que define un TableAdapter se vuelve a generar cuando se realizan cambios en el TableAdapter en el **Diseñador de DataSet**, o cuando un asistente modifica la configuración de un TableAdapter. Para evitar que se elimine el código durante la regeneración de un TableAdapter, agregue código al archivo de clase parcial del TableAdapter.

 Las clases parciales permiten que el código de una clase específica se divida entre varios archivos físicos. Para obtener más información, vea [partial](https://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448) o [partial (Type)](https://msdn.microsoft.com/library/27320743-a22e-4c7b-b0b3-53afe3607334).

## <a name="locate-tableadapters-in-code"></a>Buscar TableAdapters en el código
 Aunque los TableAdapters están diseñados con el **Diseñador de DataSet**, las clases de TableAdapter que se generan no son clases anidadas de <xref:System.Data.DataSet> . Los TableAdapters se encuentran en un espacio de nombres basado en el nombre del conjunto de objetos asociado del TableAdapter. Por ejemplo, si la aplicación contiene un conjunto de `HRDataSet` objetos denominado, los TableAdapters se ubicarían en el `HRDataSetTableAdapters` espacio de nombres. (La Convención de nomenclatura sigue este patrón: *DatasetName*  +  `TableAdapters` ).

 En el ejemplo siguiente se supone que un TableAdapter denominado `CustomersTableAdapter` está en un proyecto con `NorthwindDataSet` .

#### <a name="to-create-a-partial-class-for-a-tableadapter"></a>Para crear una clase parcial para un TableAdapter

1. Agregue una nueva clase al proyecto; para ello, vaya al menú **proyecto** y seleccione**Agregar clase**.

2. Asigne `CustomersTableAdapterExtended` como nombre de la clase.

3. Seleccione **Agregar**.

4. Reemplace el código por el espacio de nombres correcto y el nombre de clase parcial del proyecto como se indica a continuación:

     [!code-csharp[VbRaddataTableAdapters#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/CustomersTableAdapterExtended.cs#2)]
     [!code-vb[VbRaddataTableAdapters#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/CustomersTableAdapterExtended.vb#2)]

## <a name="see-also"></a>Consulte también
 [Rellenar conjuntos de datos mediante TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)
