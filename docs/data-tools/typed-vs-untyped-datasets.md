---
title: Escrito frente a los conjuntos de datos sin tipo | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: c83ba0bb-5425-4d47-8891-6b4dbf937701
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 7c55b160012997281cd5e7551ea07178b63f0fca
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="typed-vs-untyped-datasets"></a>Escrito frente a los conjuntos de datos sin tipo
Un conjunto de datos con tipo es un conjunto de datos que primero se deriva de la base de <xref:System.Data.DataSet> clase y, a continuación, usa información de la **Diseñador de Dataset**, que está almacenado en un archivo .xsd, para generar un nuevo establecimiento inflexible de tipos dataset (clase). La información del esquema (tablas, columnas etc.) se genera y se compila en esta nueva clase de conjunto de datos como un conjunto de propiedades y objetos de primera clase. Puesto que un conjunto de datos con tipo hereda de la base de <xref:System.Data.DataSet> (clase), la clase con tipo asume toda la funcionalidad de la <xref:System.Data.DataSet> clase y puede usarse con métodos que toman una instancia de un <xref:System.Data.DataSet> clase como un parámetro.  
  
 Un conjunto de datos sin tipo, en cambio, no tiene ningún esquema integrado correspondiente. Como en un conjunto de datos con tipo, un conjunto de datos sin tipo contiene tablas, columnas y así sucesivamente, pero las que sólo se exponen como colecciones. (Sin embargo, después de crear manualmente las tablas y otros elementos de datos en un conjunto de datos sin tipo, puede exportar estructura del conjunto de datos como un esquema con el conjunto de datos <xref:System.Data.DataSet.WriteXmlSchema%2A> método.)  
  
## <a name="contrasting-data-access-in-typed-and-untyped-datasets"></a>Acceso a datos en conjuntos de datos con tipo y sin tipo de contraste  
 La clase para un conjunto de datos con tipo tiene un modelo de objetos en la que sus propiedades asumen los nombres reales de las tablas y columnas. Por ejemplo, si está trabajando con un conjunto de datos con tipo, se puede hacer referencia a una columna mediante código como el siguiente:  
  
 [!code-csharp[VbRaddataDatasets#4](../data-tools/codesnippet/CSharp/typed-vs-untyped-datasets_1.cs)]
 [!code-vb[VbRaddataDatasets#4](../data-tools/codesnippet/VisualBasic/typed-vs-untyped-datasets_1.vb)]  
  
 En cambio, si está trabajando con un conjunto de datos sin tipo, el código equivalente es:  
  
 [!code-csharp[VbRaddataDatasets#5](../data-tools/codesnippet/CSharp/typed-vs-untyped-datasets_2.cs)]
 [!code-vb[VbRaddataDatasets#5](../data-tools/codesnippet/VisualBasic/typed-vs-untyped-datasets_2.vb)]  
  
 Acceso con tipo no sólo es más fácil de leer, pero también totalmente compatible con IntelliSense en el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **Editor de código**. Además de ser más fácil trabajar con, la sintaxis para el conjunto de datos con tipo proporciona comprobación de tipos en tiempo de compilación, reduce enormemente la posibilidad de errores de asignación de valores a los miembros del conjunto de datos. Si cambia el nombre de una columna en su <xref:System.Data.DataSet> clase y, a continuación, compile la aplicación, recibirá un error de compilación. Haga doble clic en el error de compilación en el **lista de tareas**, puede ir directamente a la línea o líneas de código que haga referencia al nombre de columna anterior. Acceso a tablas y columnas de un conjunto de datos también es un poco más rápido en tiempo de ejecución porque el acceso se determina en tiempo de compilación, no a través de colecciones en tiempo de ejecución.  
  
 Aunque los conjuntos de datos tienen muchas ventajas, un conjunto de datos sin tipo resulta útil en una variedad de circunstancias. El escenario más obvio es cuando no hay ningún esquema para el conjunto de datos. Esto puede ocurrir, por ejemplo, si la aplicación está interactuando con un componente que devuelve un conjunto de datos, pero no sabe de antemano ¿cuál es su estructura. De forma similar, hay ocasiones cuando se trabaja con datos que no tiene una estructura estática y predecible. En ese caso, es práctico utilizar un conjunto de datos con tipo, ya que tendría que volver a generar la clase de conjunto de datos con tipo con cada cambio realizado en la estructura de datos.  
  
 Por lo general, hay muchas veces puede crear un conjunto de datos de forma dinámica sin disponer de un esquema. En ese caso, el conjunto de datos es simplemente una estructura adecuada en el que puede mantener información, siempre y cuando los datos se pueden representar de forma relacional. Al mismo tiempo, puede aprovechar las capacidades del conjunto de datos, como la capacidad de serializar la información para pasar a otro proceso, o escribir un archivo XML.

## <a name="see-also"></a>Vea también
[Herramientas de conjunto de datos](../data-tools/dataset-tools-in-visual-studio.md)