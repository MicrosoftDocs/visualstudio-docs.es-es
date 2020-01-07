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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 3198b94b1248f20b178e85e9e75a2765e6191c28
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586307"
---
# <a name="save-a-dataset-as-xml"></a>Guardar un conjunto de datos como XML

Obtener acceso a los datos XML de un conjunto de datos mediante una llamada a los métodos XML disponibles en el conjunto de datos. Para guardar los datos en formato XML, puede llamar al método <xref:System.Data.DataSet.GetXml%2A> o al método <xref:System.Data.DataSet.WriteXml%2A> de una <xref:System.Data.DataSet>.

La llamada al método <xref:System.Data.DataSet.GetXml%2A> devuelve una cadena que contiene los datos de todas las tablas de datos del conjunto de datos con formato XML.

Al llamar al método <xref:System.Data.DataSet.WriteXml%2A> se envían los datos con formato XML a un archivo que se especifique.

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>Para guardar los datos de un conjunto de datos como XML en una variable

- El método <xref:System.Data.DataSet.GetXml%2A> devuelve un objeto <xref:System.String>. Declare una variable de tipo <xref:System.String> y asígnele los resultados del método <xref:System.Data.DataSet.GetXml%2A>.

     [!code-vb[VbRaddataSaving#12](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_1.vb)]
     [!code-csharp[VbRaddataSaving#12](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_1.cs)]

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>Para guardar los datos de un conjunto de datos como XML en un archivo

- El método <xref:System.Data.DataSet.WriteXml%2A> tiene varias sobrecargas. Declare una variable y asígnela una ruta de acceso válida para guardar el archivo. En el código siguiente se muestra cómo guardar los datos en un archivo:

     [!code-vb[VbRaddataSaving#13](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_2.vb)]
     [!code-csharp[VbRaddataSaving#13](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_2.cs)]

## <a name="see-also"></a>Vea también

- [Guardar los datos de nuevo en la base de datos](../data-tools/save-data-back-to-the-database.md)
