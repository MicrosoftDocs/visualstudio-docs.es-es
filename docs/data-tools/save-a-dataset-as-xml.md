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
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 5a1b0c453f3b48b12c5a77fce86789a66fe77c26
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174002"
---
# <a name="save-a-dataset-as-xml"></a>Guardar un conjunto de datos como XML

Tener acceso a los datos XML en un conjunto de datos mediante una llamada a los métodos XML disponibles en el conjunto de datos. Para guardar los datos en formato XML, puede llamar el <xref:System.Data.DataSet.GetXml%2A> método o la <xref:System.Data.DataSet.WriteXml%2A> método de un <xref:System.Data.DataSet>.

Una llamada a la <xref:System.Data.DataSet.GetXml%2A> método devuelve una cadena que contiene los datos de todas las tablas de datos del conjunto de datos con formato XML.

Una llamada a la <xref:System.Data.DataSet.WriteXml%2A> método envía los datos con formato XML en un archivo que especifique.

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>Para guardar los datos en un conjunto de datos como XML en una variable

- El <xref:System.Data.DataSet.GetXml%2A> método devuelve un <xref:System.String>. Declarar una variable de tipo <xref:System.String> y asignarle los resultados de la <xref:System.Data.DataSet.GetXml%2A> método.

     [!code-vb[VbRaddataSaving#12](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_1.vb)]
     [!code-csharp[VbRaddataSaving#12](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_1.cs)]

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>Para guardar los datos en un conjunto de datos como XML en un archivo

- El <xref:System.Data.DataSet.WriteXml%2A> método tiene varias sobrecargas. Declarar una variable y asigne una ruta válida a guardar el archivo. El código siguiente muestra cómo guardar los datos en un archivo:

     [!code-vb[VbRaddataSaving#13](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_2.vb)]
     [!code-csharp[VbRaddataSaving#13](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_2.cs)]

## <a name="see-also"></a>Vea también

- [Guardar los datos de nuevo en la base de datos](../data-tools/save-data-back-to-the-database.md)