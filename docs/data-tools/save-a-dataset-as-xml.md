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
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 3c993ac8703468a24a99e114563fec1bdc817581
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55913124"
---
# <a name="save-a-dataset-as-xml"></a>Guardar un conjunto de datos como XML

Tener acceso a los datos XML en un conjunto de datos mediante una llamada a los métodos XML disponibles en el conjunto de datos. Para guardar los datos en formato XML, puede llamar el <xref:System.Data.DataSet.GetXml%2A> método o la <xref:System.Data.DataSet.WriteXml%2A> método de un <xref:System.Data.DataSet>.

Una llamada a la <xref:System.Data.DataSet.GetXml%2A> método devuelve una cadena que contiene los datos de todas las tablas de datos del conjunto de datos con formato XML.

Una llamada a la <xref:System.Data.DataSet.WriteXml%2A> método envía los datos con formato XML en un archivo que especifique.

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>Para guardar los datos en un conjunto de datos como XML en una variable

- El método <xref:System.Data.DataSet.GetXml%2A> devuelve un objeto <xref:System.String>. Declarar una variable de tipo <xref:System.String> y asignarle los resultados de la <xref:System.Data.DataSet.GetXml%2A> método.

     [!code-vb[VbRaddataSaving#12](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_1.vb)]
     [!code-csharp[VbRaddataSaving#12](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_1.cs)]

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>Para guardar los datos en un conjunto de datos como XML en un archivo

- El <xref:System.Data.DataSet.WriteXml%2A> método tiene varias sobrecargas. Declarar una variable y asigne una ruta válida a guardar el archivo. El código siguiente muestra cómo guardar los datos en un archivo:

     [!code-vb[VbRaddataSaving#13](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_2.vb)]
     [!code-csharp[VbRaddataSaving#13](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_2.cs)]

## <a name="see-also"></a>Vea también

- [Guardar los datos de nuevo en la base de datos](../data-tools/save-data-back-to-the-database.md)