---
title: Herramientas de conjunto de datos
ms.date: 11/21/2018
ms.topic: conceptual
f1_keywords:
- vs.data.DataSet
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: cb41a4e3e4ed1c0032c579779a18c7df0bc22477
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "75586723"
---
# <a name="dataset-tools-in-visual-studio"></a>Herramientas de conjunto de datos en Visual Studio

> [!NOTE]
> Los conjuntos de datos y las clases relacionadas son tecnologías de .NET heredadas de la 2000s temprana que permiten a las aplicaciones trabajar con los datos en memoria mientras las aplicaciones se desconectan de la base de datos. Son especialmente útiles para las aplicaciones que permiten a los usuarios modificar datos y guardar los cambios de nuevo en la base de datos. Aunque los conjuntos de valores han demostrado ser una tecnología muy eficaz, se recomienda que las aplicaciones .NET nuevas utilicen Entity Framework. Entity Framework proporciona una forma más natural de trabajar con datos tabulares como modelos de objetos y tiene una interfaz de programación más sencilla.

Un `DataSet` objeto es un objeto en memoria que es esencialmente una pequeña base de datos. Contiene `DataTable` objetos, `DataColumn` y `DataRow` en los que puede almacenar y modificar datos de una o varias bases de datos sin tener que mantener una conexión abierta. El conjunto de datos mantiene información acerca de los cambios en sus datos, por lo que se puede realizar un seguimiento de las actualizaciones y enviarlas de nuevo a la base de datos cuando la aplicación se vuelve a conectar.

Los conjuntos de valores y las clases relacionadas se definen en el <xref:System.Data?displayProperty=fullName> espacio de nombres de la API de .net. Puede crear y modificar conjuntos de valores de forma dinámica en el código mediante ADO.NET. En la documentación de esta sección se muestra cómo trabajar con conjuntos de información mediante los diseñadores de Visual Studio. Los conjuntos de datos que se crean a través de diseñadores utilizan objetos **TableAdapter** para interactuar con la base de datos. Los conjuntos de valores creados mediante programación usan objetos **DataAdapter** . Para obtener información sobre cómo crear conjuntos de datos mediante programación, vea [DataAdapters y DataReader](/dotnet/framework/data/adonet/dataadapters-and-datareaders).

Si la aplicación solo necesita leer datos de una base de datos y no realizar actualizaciones, adiciones o eliminaciones, normalmente puede obtener un mejor rendimiento si usa un `DataReader` objeto para recuperar datos en un `List` objeto genérico u otro objeto de colección. Si va a mostrar los datos, puede enlazar los datos a la interfaz de usuario.

## <a name="dataset-workflow"></a>Flujo de trabajo de DataSet

Visual Studio proporciona herramientas para simplificar el trabajo con conjuntos de objetos. El flujo de trabajo de un extremo a otro básico es:

- Use la [ventana orígenes de datos](add-new-data-sources.md#data-sources-window) para crear un nuevo conjunto de datos a partir de uno o más orígenes de datos. Use el **Diseñador de DataSet** para configurar el conjunto de DataSet y establecer sus propiedades. Por ejemplo, debe especificar las tablas del origen de datos que se van a incluir y las columnas de cada tabla. Elija cuidadosamente para conservar la cantidad de memoria que requiere el conjunto de DataSet. Para obtener más información, vea [Crear y configurar conjuntos de datos](../data-tools/create-and-configure-datasets-in-visual-studio.md).

- Especifique las relaciones entre las tablas para que las claves externas se controlen correctamente. Para obtener más información, vea [rellenar conjuntos de datos mediante TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md).

- Use el **Asistente** para la configuración de TableAdapter para especificar la consulta o el procedimiento almacenado que rellena el conjunto de datos y las operaciones de base de datos (actualización, eliminación, etc.) que se van a implementar. Para más información, consulte los temas siguientes:

  - [Rellenar conjuntos de datos mediante TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)

  - [Editar datos en conjuntos de datos](../data-tools/edit-data-in-datasets.md)

  - [Validar los datos en conjuntos de datos](../data-tools/validate-data-in-datasets.md)

  - [Guardar los datos de nuevo en la base de datos](../data-tools/save-data-back-to-the-database.md)

- Consulte y busque en los datos del conjunto de datos. Para obtener más información, vea [consultas de conjuntos](../data-tools/query-datasets.md)de datos. [!INCLUDE[linq_dataset](../data-tools/includes/linq_dataset_md.md)] habilita [LINQ (Language-Integrated Query)](/dotnet/csharp/linq/) sobre los datos de un <xref:System.Data.DataSet> objeto. Para más información, vea [LINQ to DataSet](/dotnet/framework/data/adonet/linq-to-dataset).

- Utilice la ventana **orígenes de datos** para enlazar los controles de la interfaz de usuario al conjunto de datos o sus columnas individuales, y para especificar las columnas que son editables por el usuario. Para obtener más información, vea [enlazar controles a datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

## <a name="datasets-and-n-tier-architecture"></a>Conjuntos de valores y arquitectura de N niveles

Para obtener información acerca de los conjuntos de datos en aplicaciones de N niveles, consulte [trabajar con conjuntos de datos en aplicaciones de n niveles](../data-tools/work-with-datasets-in-n-tier-applications.md).

## <a name="datasets-and-xml"></a>Conjuntos de valores y XML

Para obtener información sobre la conversión de conjuntos de datos a y desde XML, vea [leer datos XML en un conjunto de datos](../data-tools/read-xml-data-into-a-dataset.md) y [guardar un conjunto de datos como XML](../data-tools/save-a-dataset-as-xml.md).

## <a name="see-also"></a>Vea también

- [Visual Studio Data Tools para .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
