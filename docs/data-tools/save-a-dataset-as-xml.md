---
title: Guardar un conjunto de datos como XML
description: Guardar un conjunto de DataSet como XML. Obtener acceso a los datos XML de un conjunto de datos mediante una llamada a los métodos XML disponibles en el conjunto de datos, como GetXml o WriteXml.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML [Visual Basic], datasets
- data [Visual Studio], saving as XML
- datasets [Visual Basic], saving as XML
- saving data
ms.assetid: 68b8327c-ae05-49ff-b9ba-99183e70b52c
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 9030740a25312ea1463b950e34061884e9487ba4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858532"
---
# <a name="save-a-dataset-as-xml"></a>Guardar un conjunto de datos como XML

Obtener acceso a los datos XML de un conjunto de datos mediante una llamada a los métodos XML disponibles en el conjunto de datos. Para guardar los datos en formato XML, puede llamar al <xref:System.Data.DataSet.GetXml%2A> método o al <xref:System.Data.DataSet.WriteXml%2A> método de <xref:System.Data.DataSet> .

La llamada al <xref:System.Data.DataSet.GetXml%2A> método devuelve una cadena que contiene los datos de todas las tablas de datos del conjunto de datos con formato XML.

La llamada al <xref:System.Data.DataSet.WriteXml%2A> método envía los datos con formato XML a un archivo que especifique.

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>Para guardar los datos de un conjunto de datos como XML en una variable

- El método <xref:System.Data.DataSet.GetXml%2A> devuelve una instancia de <xref:System.String>. Declare una variable de tipo <xref:System.String> y asígnele los resultados del <xref:System.Data.DataSet.GetXml%2A> método.

     [!code-vb[VbRaddataSaving#12](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_1.vb)]
     [!code-csharp[VbRaddataSaving#12](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_1.cs)]

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>Para guardar los datos de un conjunto de datos como XML en un archivo

- El <xref:System.Data.DataSet.WriteXml%2A> método tiene varias sobrecargas. Declare una variable y asígnela una ruta de acceso válida para guardar el archivo. En el código siguiente se muestra cómo guardar los datos en un archivo:

     [!code-vb[VbRaddataSaving#13](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_2.vb)]
     [!code-csharp[VbRaddataSaving#13](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_2.cs)]

## <a name="see-also"></a>Vea también

- [Guardar los datos de nuevo en la base de datos](../data-tools/save-data-back-to-the-database.md)
