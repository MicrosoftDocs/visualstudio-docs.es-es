---
title: Herramientas de conjunto de datos
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
f1_keywords:
- vs.data.DataSet
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- untyped datasets
- datasets [Visual Basic], extended properties
- typed datasets
- current record in dataset
- XML [Visual Basic], datasets
- DataSet class, about datasets
- unique constraints (datasets)
- data relationships
- parent records in datasets
- extended properties, in typed datasets
- datasets [Visual Basic]
- schemas [Visual Basic], datasets
- datasets [Visual Basic], msprop
- master-detail tables, datasets
- databases [Visual Basic], updating
- msprop
- foreign keys, datasets
- DataSet class
- datasets [Visual Basic], filling
- case sensitivity, datasets
- constraints [Visual Basic], datasets
- child records
- related tables, datasets
- updating datasets, about dataset updates
- data caching, datasets
- DataRelation object, datasets
- untyped datasets, compared to typed datasets
- cache [Visual Studio], datasets
- datasets [Visual Basic], relationships
- related tables
- XML schemas, about XML schemas and datasets
- relationships, datasets
- typed datasets, compared to untyped datasets
- datasets [Visual Basic], populating
- datasets [Visual Basic], namespace
- data adapters, populating datasets
ms.assetid: ee57f4f6-9fe1-4e0a-be9a-955c486ff427
caps.latest.revision: 53
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 23e4deba53288383a569f6da6e14d27f723825ee
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657383"
---
# <a name="dataset-tools-in-visual-studio"></a>Herramientas de conjunto de datos en Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

NOTA]
> Los conjuntos de datos y las clases relacionadas son tecnologías de .NET heredadas de la 2000s temprana que permiten a las aplicaciones trabajar con los datos en memoria mientras las aplicaciones se desconectan de la base de datos. Son especialmente útiles para las aplicaciones que permiten a los usuarios modificar datos y guardar los cambios de nuevo en la base de datos. Aunque los conjuntos de valores han demostrado ser una tecnología muy eficaz, se recomienda que las aplicaciones .NET nuevas utilicen Entity Framework. Entity Framework proporciona una forma más natural de trabajar con datos tabulares como modelos de objetos y tiene una interfaz de programación más sencilla.

 Un objeto DataSet es un objeto en memoria que es esencialmente una base de datos pequeña. Contiene objetos DataTable, DataColumn y DataRow en los que puede almacenar y modificar datos de una o varias bases de datos sin tener que mantener una conexión abierta. El conjunto de datos mantiene información acerca de los cambios en sus datos, por lo que se puede realizar un seguimiento de las actualizaciones y enviarlas de nuevo a la base de datos cuando la aplicación se vuelve a conectar.

 Los conjuntos de datos y las clases relacionadas se definen en el espacio de nombres System. Data de la biblioteca de clases de .NET Framework. Puede crear y modificar los conjuntos de valores de forma dinámica en el código. Para obtener más información sobre cómo hacerlo, vea ADO.NET. En la documentación de esta sección se muestra cómo trabajar con conjuntos de información mediante los diseñadores de Visual Studio. Lo que debe saber: los conjuntos de datos que se realizan a través de diseñadores utilizan objetos TableAdapter para interactuar con la base de datos, mientras que los conjuntos de datos que se realizan mediante programación usan objetos DataAdapter. Para obtener información sobre cómo crear conjuntos de datos mediante programación, vea [DataAdapters y DataReader](https://msdn.microsoft.com/library/cc952ca2-ec19-46ab-9189-15174b52cb74).

 Si la aplicación solo necesita leer datos de una base de datos y no realizar actualizaciones, adiciones o eliminaciones, normalmente puede obtener un mejor rendimiento si usa un objeto DataReader para recuperar datos en un objeto de lista genérico u otro objeto de colección. Si va a mostrar los datos, puede enlazar los datos a la interfaz de usuario.

## <a name="dataset-workflow"></a>Flujo de trabajo de DataSet
 Visual Studio proporciona muchas herramientas para simplificar el trabajo con conjuntos de objetos. El flujo de trabajo de un extremo a otro básico es:

- Utilice la ventana **origen de datos** para crear un nuevo conjunto de datos a partir de uno o más orígenes de datos. Use el **Diseñador de DataSet** para configurar el conjunto de DataSet y establecer sus propiedades. Por ejemplo, debe especificar las tablas del origen de datos que se van a incluir y las columnas de cada tabla. Elija cuidadosamente para conservar la cantidad de memoria que requerirá el conjunto de DataSet. Para obtener más información, vea [Crear y configurar conjuntos de datos](../data-tools/create-and-configure-datasets-in-visual-studio.md).

- Especifique las relaciones entre las tablas para que las claves externas se controlen correctamente. Para obtener más información, vea [rellenar conjuntos de datos mediante TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md).

- Use el **Asistente para configuración de TableAdapter** para especificar la consulta o el procedimiento almacenado que rellenará el conjunto de datos y las operaciones de base de datos (actualización, eliminación, etc.) que se van a implementar. Para obtener más información, consulte estos temas:

  - [Llenar conjuntos de datos mediante TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)

  - [Editar datos en conjuntos de datos](../data-tools/edit-data-in-datasets.md)

  - [Validar los datos en conjuntos de datos](../data-tools/validate-data-in-datasets.md)

  - [Guardar los datos de nuevo en la base de datos](../data-tools/save-data-back-to-the-database.md)

- Consulte y busque en los datos del conjunto de datos. Para obtener más información, vea [consultas de conjuntos](../data-tools/query-datasets.md)de datos. [!INCLUDE[linq_dataset](../includes/linq-dataset-md.md)] habilita [LINQ (Language-Integrated Query)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) sobre los datos de un objeto <xref:System.Data.DataSet>. Para más información, vea [LINQ to DataSet](https://msdn.microsoft.com/library/743e3755-3ecb-45a2-8d9b-9ed41f0dcf17).

- Utilice la ventana **orígenes de datos** para enlazar los controles de la interfaz de usuario al conjunto de datos o sus columnas individuales, y para especificar las columnas que son editables por el usuario. Para obtener más información, vea [enlazar controles a datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

## <a name="datasets-and-n-tier-architecture"></a>Conjuntos de valores y arquitectura de N niveles
 Para obtener información acerca de los conjuntos de datos en aplicaciones de N niveles, consulte [trabajar con conjuntos de datos en aplicaciones de n niveles](../data-tools/work-with-datasets-in-n-tier-applications.md).

## <a name="datasets-and-xml"></a>Conjuntos de valores y XML
 Para obtener información sobre la conversión de conjuntos de datos a y desde XML, vea [leer datos XML en un conjunto de datos](../data-tools/read-xml-data-into-a-dataset.md) y [guardar un conjunto de datos como XML](../data-tools/save-a-dataset-as-xml.md).

## <a name="see-also"></a>Vea también
 [Visual Studio Data Tools para .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
