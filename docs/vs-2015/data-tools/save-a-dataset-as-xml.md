---
title: Guardar un conjunto de datos como XML | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- XML [Visual Basic], datasets
- data [Visual Studio], saving as XML
- datasets [Visual Basic], saving as XML
- saving data
ms.assetid: 68b8327c-ae05-49ff-b9ba-99183e70b52c
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a91bc594f2f028f7dfc7a11263b7aac23150b7f5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49287578"
---
# <a name="save-a-dataset-as-xml"></a>Guardar un conjunto de datos como XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Los datos XML en un conjunto de datos pueden tener acceso mediante una llamada a los métodos XML disponibles en el conjunto de datos. Para guardar los datos en formato XML, puede llamar el <xref:System.Data.DataSet.GetXml%2A> método o la <xref:System.Data.DataSet.WriteXml%2A> método de un <xref:System.Data.DataSet>.  
  
 Una llamada a la <xref:System.Data.DataSet.GetXml%2A> método devuelve una cadena que contiene los datos de todas las tablas de datos del conjunto de datos con formato XML.  
  
 Una llamada a la <xref:System.Data.DataSet.WriteXml%2A> método envía los datos con formato XML en un archivo que especifique.  
  
### <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>Para guardar los datos en un conjunto de datos como XML en una variable  
  
-   El <xref:System.Data.DataSet.GetXml%2A> método devuelve un <xref:System.String>. Esto significa que declarar una variable de tipo <xref:System.String> y asignarle los resultados de la <xref:System.Data.DataSet.GetXml%2A> método.  
  
     [!code-csharp[VbRaddataSaving#12](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#12)]
     [!code-vb[VbRaddataSaving#12](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#12)]  
  
### <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>Para guardar los datos en un conjunto de datos como XML en un archivo  
  
-   El <xref:System.Data.DataSet.WriteXml%2A> método tiene varias sobrecargas. El código siguiente muestra cómo guardar los datos en un archivo. Declarar una variable y asigne una ruta válida a guardar el archivo.  
  
     [!code-csharp[VbRaddataSaving#13](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#13)]
     [!code-vb[VbRaddataSaving#13](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#13)]  
  
## <a name="see-also"></a>Vea también  
 [Guardar los datos de nuevo en la base de datos](../data-tools/save-data-back-to-the-database.md)

