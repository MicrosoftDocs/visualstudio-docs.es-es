---
title: Guardar un conjunto de datos como XML | Documentos de Microsoft
ms.custom: ''
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
ms.openlocfilehash: b9d91e964ddade89c8bce8f0519517995b7d75a0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="save-a-dataset-as-xml"></a>Guardar un conjunto de datos como XML
Pueden tener acceso a los datos XML en un conjunto de datos mediante una llamada a los métodos XML disponibles en el conjunto de datos. Para guardar los datos en formato XML, se puede llamar a la <xref:System.Data.DataSet.GetXml%2A> método o la <xref:System.Data.DataSet.WriteXml%2A> método de un <xref:System.Data.DataSet>.  
  
 Llamar a la <xref:System.Data.DataSet.GetXml%2A> método devuelve una cadena que contiene los datos de todas las tablas de datos en el conjunto de datos que tenga el mismo formato XML.  
  
 Llamar a la <xref:System.Data.DataSet.WriteXml%2A> método envía los datos con formato XML en un archivo que especifique.  
  
### <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>Para guardar los datos en un conjunto de datos como XML en una variable  
  
-   El <xref:System.Data.DataSet.GetXml%2A> método devuelve un <xref:System.String>. Esto significa que se declara una variable de tipo <xref:System.String> y asignar los resultados de la <xref:System.Data.DataSet.GetXml%2A> método.  
  
     [!code-vb[VbRaddataSaving#12](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_1.vb)]
     [!code-csharp[VbRaddataSaving#12](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_1.cs)]  
  
### <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>Para guardar los datos en un conjunto de datos como XML en un archivo  
  
-   El <xref:System.Data.DataSet.WriteXml%2A> método tiene varias sobrecargas. El código siguiente muestra cómo guardar los datos en un archivo. Declare una variable y asignar una ruta de acceso válida para guardar el archivo.  
  
     [!code-vb[VbRaddataSaving#13](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_2.vb)]
     [!code-csharp[VbRaddataSaving#13](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_2.cs)]  
  
## <a name="see-also"></a>Vea también  
 [Guardar los datos de nuevo en la base de datos](../data-tools/save-data-back-to-the-database.md)