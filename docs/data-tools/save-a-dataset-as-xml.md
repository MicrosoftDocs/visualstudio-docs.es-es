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
ms.openlocfilehash: 42974852a3051fd3473b6b23d880eeb38b966b95
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216207"
---
# <a name="save-a-dataset-as-xml"></a>Guardar un conjunto de datos como XML

Obtener acceso a los datos XML de un conjunto de datos mediante una llamada a los métodos XML disponibles en el conjunto de datos. Para guardar los datos en formato XML, puede llamar al <xref:System.Data.DataSet.GetXml%2A> método o al <xref:System.Data.DataSet.WriteXml%2A> método de <xref:System.Data.DataSet> .

La llamada al <xref:System.Data.DataSet.GetXml%2A> método devuelve una cadena que contiene los datos de todas las tablas de datos del conjunto de datos con formato XML.

La llamada al <xref:System.Data.DataSet.WriteXml%2A> método envía los datos con formato XML a un archivo que especifique.

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>Para guardar los datos de un conjunto de datos como XML en una variable

- El método <xref:System.Data.DataSet.GetXml%2A> devuelve una instancia de <xref:System.String>. Declare una variable de tipo <xref:System.String> y asígnele los resultados del <xref:System.Data.DataSet.GetXml%2A> método.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb" id="Snippet12":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs" id="Snippet12":::

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>Para guardar los datos de un conjunto de datos como XML en un archivo

- El <xref:System.Data.DataSet.WriteXml%2A> método tiene varias sobrecargas. Declare una variable y asígnela una ruta de acceso válida para guardar el archivo. En el código siguiente se muestra cómo guardar los datos en un archivo:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb" id="Snippet13":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs" id="Snippet13":::

## <a name="see-also"></a>Consulte también

- [Guardar los datos de nuevo en la base de datos](../data-tools/save-data-back-to-the-database.md)
