---
title: Herramientas de conjunto de datos en Visual Studio | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.data.DataSet
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
caps.latest.revision: "49"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 0a589cf48f53636bcd3892c7c4c991e0fb516bf3
ms.sourcegitcommit: f0ddee934713ea9126fa107018a57a94a05eafd3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/12/2017
---
# <a name="dataset-tools-in-visual-studio"></a>Herramientas de conjunto de datos en Visual Studio
> [!NOTE]
>  Conjuntos de datos y las clases relacionadas son tecnologías .NET heredadas de los años 2000 temprano que permiten que las aplicaciones trabajar con datos en memoria mientras las aplicaciones están desconectadas de la base de datos. Son especialmente útiles para las aplicaciones que permiten a los usuarios modificar los datos y conservar los cambios a la base de datos. Aunque los conjuntos de datos han demostrado que una tecnología muy correcta, se recomienda que las nuevas aplicaciones .NET utilizar Entity Framework. Entity Framework proporciona una forma más natural de trabajar con datos tabulares como modelos de objetos, y tiene una interfaz de programación más sencilla.  
  
 Un objeto de conjunto de datos es un objeto en memoria que es básicamente una base de datos mínima. Contiene los objetos DataRow, DataTable y DataColumn en el que puede almacenar y modificar los datos de una o varias bases de datos sin tener que mantener abierta una conexión. El conjunto de datos mantiene información sobre los cambios en sus datos, por lo que las actualizaciones pueden controlarse y envía a la base de datos cuando se vuelve a conectar la aplicación.  
  
 Conjuntos de datos y las clases relacionadas se definen en el espacio de nombres System.Data en la biblioteca de clases de .NET Framework. Puede crear y modificar conjuntos de datos dinámicamente en el código. Para obtener más información acerca de cómo hacerlo, vea ADO.NET. La documentación de esta sección muestra cómo trabajar con conjuntos de datos mediante el uso de diseñadores de Visual Studio. Hay que saber: conjuntos de datos que se realizan a través de los diseñadores utilizan objetos de TableAdapter para interactuar con la base de datos, mientras que los conjuntos de datos que se realizan mediante programación usan objetos DataAdapter. Para obtener información acerca de cómo crear conjuntos de datos mediante programación, vea [objetos DataAdapter y DataReader](/dotnet/framework/data/adonet/dataadapters-and-datareaders).  
  
 Si la aplicación necesita sólo leer datos de una base de datos y no realizar actualizaciones, se agrega o se elimina, normalmente puede obtener un rendimiento mejor mediante un objeto DataReader para recuperar datos en un objeto de lista genérico o de otro objeto de colección. Si va a mostrar los datos, también puede enlazar la interfaz de usuario a la colección.  
  
## <a name="dataset-workflow"></a>Flujo de trabajo del conjunto de datos  
 Visual Studio proporciona muchas herramientas que simplifican el trabajo con conjuntos de datos. El flujo de trabajo de extremo a extremo básica es:  
  
-   Use la **origen de datos** ventana para crear un nuevo conjunto de datos de uno o más orígenes de datos. Use la **Diseñador de Dataset** para configurar el conjunto de datos y establecer sus propiedades. Por ejemplo, debe especificar las tablas del origen de datos para incluir y qué columnas de cada tabla. Elija cuidadosamente conservar la cantidad de memoria que requerirá el conjunto de datos. Para obtener más información, vea [Crear y configurar conjuntos de datos](../data-tools/create-and-configure-datasets-in-visual-studio.md).  
  
-   Especificar las relaciones entre las tablas para que las claves externas se controlen correctamente. Para obtener más información, consulte [rellenar conjuntos de datos mediante el uso de los TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md).  
  
-   Use la **Asistente para configuración de TableAdapter** para especificar la consulta o el procedimiento almacenado que rellenará el conjunto de datos y qué operaciones de base de datos (update, delete etc.) para implementar. Para obtener más información, consulte estos temas:  
  
    -   [Llenar conjuntos de datos mediante TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)  
  
    -   [Editar datos en conjuntos de datos](../data-tools/edit-data-in-datasets.md)  
  
    -   [Validar los datos en conjuntos de datos](../data-tools/validate-data-in-datasets.md)  
  
    -   [Guardar los datos de nuevo en la base de datos](../data-tools/save-data-back-to-the-database.md)  
  
-   Consultar y buscar los datos en el conjunto de datos. Para obtener más información, consulte [consultar conjuntos de datos](../data-tools/query-datasets.md). [!INCLUDE[linq_dataset](../data-tools/includes/linq_dataset_md.md)]permite [LINQ (Language-Integrated Query)](/dotnet/csharp/linq/) sobre los datos en un <xref:System.Data.DataSet> objeto. Para más información, vea [LINQ to DataSet](/dotnet/framework/data/adonet/linq-to-dataset).  
  
-   Use la **orígenes de datos** ventana para enlazar controles de interfaz de usuario para el conjunto de datos o sus columnas individuales y para especificar qué columnas se puede modificar el usuario. Para obtener más información, consulte [enlazar controles a datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
## <a name="datasets-and-n-tier-architecture"></a>Arquitectura de conjuntos de datos y con N niveles  
 Para obtener información acerca de los conjuntos de datos en aplicaciones de N niveles, vea [trabajar con conjuntos de datos en aplicaciones de n niveles](../data-tools/work-with-datasets-in-n-tier-applications.md).  
  
## <a name="datasets-and-xml"></a>Conjuntos de datos y XML  
 Para obtener información sobre cómo convertir los conjuntos de datos a y desde XML, vea [leer datos XML en un conjunto de datos](../data-tools/read-xml-data-into-a-dataset.md) y [guardar un conjunto de datos como XML](../data-tools/save-a-dataset-as-xml.md).  
  
## <a name="see-also"></a>Vea también  
 [Visual Studio Data Tools para .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)