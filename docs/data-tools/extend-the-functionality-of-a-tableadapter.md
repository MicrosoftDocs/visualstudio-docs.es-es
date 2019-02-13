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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 989eb815a6e55b5ecaed0b960963eb036b73065a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54970544"
---
# <a name="extend-the-functionality-of-a-tableadapter"></a>Ampliar la funcionalidad de un TableAdapter

Puede ampliar la funcionalidad de un TableAdapter agregando código al archivo de clase parcial del TableAdapter.

El código que define un TableAdapter se vuelve a generar cuando se realizan cambios en el TableAdapter en el **Diseñador de Dataset**, o cuando un asistente modifica la configuración de un TableAdapter. Para evitar que el código que se eliminen durante la regeneración de un TableAdapter, agregue código al archivo de clase parcial del TableAdapter.

Las clases parciales permiten que el código para una clase específica que va a dividir entre varios archivos físicos. Para obtener más información, consulte [parcial](/dotnet/visual-basic/language-reference/modifiers/partial) o [partial (tipos)](/dotnet/csharp/language-reference/keywords/partial-type).

## <a name="locate-tableadapters-in-code"></a>Busque los TableAdapters en el código

Aunque los TableAdapters están diseñados con la **Diseñador de Dataset**, las clases TableAdapter generadas no son las clases anidadas de <xref:System.Data.DataSet>. Los TableAdapters se encuentran en un espacio de nombres basado en el nombre del conjunto de datos del TableAdapter asociado. Por ejemplo, si la aplicación contiene un conjunto de datos denominado `HRDataSet`, los TableAdapters se encontrarían en el `HRDataSetTableAdapters` espacio de nombres. (La convención de nomenclatura sigue este patrón: DataSetName

En el siguiente ejemplo se da por supuesto un TableAdapter llamado `CustomersTableAdapter`está en un proyecto con `NorthwindDataSet`.

### <a name="to-create-a-partial-class-for-a-tableadapter"></a>Para crear una clase parcial para un TableAdapter

1.  Agregar una nueva clase al proyecto, vaya a la **proyecto** menú y seleccionando **Agregar clase**.

2.  Asigne a la clase el nombre `CustomersTableAdapterExtended`.

3.  Seleccione **Agregar**.

4.  Reemplace el código con el espacio de nombres correcto y el nombre de clase parcial para el proyecto como sigue:

     [!code-csharp[VbRaddataTableAdapters#2](../data-tools/codesnippet/CSharp/extend-the-functionality-of-a-tableadapter_1.cs)]
     [!code-vb[VbRaddataTableAdapters#2](../data-tools/codesnippet/VisualBasic/extend-the-functionality-of-a-tableadapter_1.vb)]

## <a name="see-also"></a>Vea también

- [Llenar conjuntos de datos mediante TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)