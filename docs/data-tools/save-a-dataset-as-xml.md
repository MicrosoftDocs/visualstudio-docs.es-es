---
title: Guardar un conjunto de datos como XML
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML [Visual Basic], datasets
- data [Visual Studio], saving as XML
- datasets [Visual Basic], saving as XML
- saving data
ms.assetid: 68b8327c-ae05-49ff-b9ba-99183e70b52c
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: b384c7d2042611be84322fd5a842f1ba5ca8de9c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="save-a-dataset-as-xml"></a>Guardar un conjunto de datos como XML

Pueden tener acceso a los datos XML en un conjunto de datos mediante una llamada a los métodos XML disponibles en el conjunto de datos. Para guardar los datos en formato XML, se puede llamar a la <xref:System.Data.DataSet.GetXml%2A> método o la <xref:System.Data.DataSet.WriteXml%2A> método de un <xref:System.Data.DataSet>.

Llamar a la <xref:System.Data.DataSet.GetXml%2A> método devuelve una cadena que contiene los datos de todas las tablas de datos en el conjunto de datos que tenga el mismo formato XML.

Llamar a la <xref:System.Data.DataSet.WriteXml%2A> método envía los datos con formato XML en un archivo que especifique.

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>Para guardar los datos en un conjunto de datos como XML en una variable

- El <xref:System.Data.DataSet.GetXml%2A> método devuelve un <xref:System.String>. Declare una variable de tipo <xref:System.String> y asignar los resultados de la <xref:System.Data.DataSet.GetXml%2A> método.

     [!code-vb[VbRaddataSaving#12](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_1.vb)]
     [!code-csharp[VbRaddataSaving#12](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_1.cs)]

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>Para guardar los datos en un conjunto de datos como XML en un archivo

- El <xref:System.Data.DataSet.WriteXml%2A> método tiene varias sobrecargas. Declare una variable y asignar una ruta de acceso válida para guardar el archivo. El código siguiente muestra cómo guardar los datos en un archivo:

     [!code-vb[VbRaddataSaving#13](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_2.vb)]
     [!code-csharp[VbRaddataSaving#13](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_2.cs)]

## <a name="see-also"></a>Vea también

- [Guardar los datos de nuevo en la base de datos](../data-tools/save-data-back-to-the-database.md)