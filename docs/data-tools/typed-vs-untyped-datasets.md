---
title: Conjuntos de datos con tipo frente a conjuntos de datos sin tipo
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: c83ba0bb-5425-4d47-8891-6b4dbf937701
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: eff5e0d2f13bfe462ff19d6cfb4e8a32a15a6064
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72639632"
---
# <a name="typed-vs-untyped-datasets"></a>Conjuntos de datos con tipo frente a conjuntos de datos sin tipo
Un conjunto de datos con tipo es un conjunto de datos que se deriva primero de la clase base <xref:System.Data.DataSet> y, a continuación, usa información del **Diseñador de DataSet**, que se almacena en un archivo. xsd, para generar una nueva clase de conjunto de datos fuertemente tipado. La información del esquema (tablas, columnas, etc.) se genera y compila en esta nueva clase de conjunto de datos como un conjunto de propiedades y objetos de primera clase. Dado que un conjunto de datos con tipo hereda de la clase <xref:System.Data.DataSet> base, la clase con tipo asume toda la funcionalidad de la clase <xref:System.Data.DataSet> y se puede usar con métodos que toman una instancia de una clase <xref:System.Data.DataSet> como parámetro.

En cambio, un conjunto de información sin tipo no tiene un esquema integrado correspondiente. Como en un conjunto de DataSet con tipo, un conjunto de información sin tipo contiene tablas, columnas, etc., pero solo se exponen como colecciones. (Sin embargo, después de crear manualmente las tablas y otros elementos de datos en un conjunto de datos sin tipo, puede exportar la estructura del conjunto de datos como un esquema mediante el método de <xref:System.Data.DataSet.WriteXmlSchema%2A> del conjunto de datos).

## <a name="contrast-data-access-in-typed-and-untyped-datasets"></a>Comparación del acceso a datos en conjuntos de datos con tipo y sin tipo
La clase para un conjunto de datos con tipo tiene un modelo de objetos en el que sus propiedades toman los nombres reales de las tablas y columnas. Por ejemplo, si está trabajando con un conjunto de DataSet con tipo, puede hacer referencia a una columna mediante código como el siguiente:

[!code-csharp[VbRaddataDatasets#4](../data-tools/codesnippet/CSharp/typed-vs-untyped-datasets_1.cs)]
[!code-vb[VbRaddataDatasets#4](../data-tools/codesnippet/VisualBasic/typed-vs-untyped-datasets_1.vb)]

Por el contrario, si está trabajando con un conjunto de información sin tipo, el código equivalente es:

[!code-csharp[VbRaddataDatasets#5](../data-tools/codesnippet/CSharp/typed-vs-untyped-datasets_2.cs)]
[!code-vb[VbRaddataDatasets#5](../data-tools/codesnippet/VisualBasic/typed-vs-untyped-datasets_2.vb)]

El acceso con tipo no solo es más fácil de leer, sino que también es totalmente compatible con IntelliSense en el **Editor de código**de Visual Studio. Además de ser más fácil de trabajar con, la sintaxis del conjunto de los tipos proporciona comprobación de tipos en tiempo de compilación, lo que reduce en gran medida la posibilidad de que se produzcan errores al asignar valores a los miembros del conjunto de elementos. Si cambia el nombre de una columna en la clase de <xref:System.Data.DataSet> y, a continuación, compila la aplicación, recibirá un error de compilación. Al hacer doble clic en el error de compilación en el **lista de tareas**, puede ir directamente a la línea o líneas de código que hacen referencia al nombre de columna anterior. El acceso a tablas y columnas en un conjunto de DataSet con tipo también es ligeramente más rápido en tiempo de ejecución porque el acceso se determina en tiempo de compilación, no a través de colecciones en tiempo de ejecución.

Aunque los conjuntos de información con tipo tienen muchas ventajas, un conjunto de información sin tipo resulta útil en diversas circunstancias. El escenario más obvio es cuando no hay ningún esquema disponible para el conjunto de DataSet. Esto puede ocurrir, por ejemplo, si la aplicación interactúa con un componente que devuelve un conjunto de elementos, pero no se sabe de antemano cuál es su estructura. Del mismo modo, hay ocasiones en las que se trabaja con datos que no tienen una estructura estática y predecible. En ese caso, no es práctico usar un conjunto de datos con tipo, porque tendría que volver a generar la clase de conjunto de datos con tipo con cada cambio en la estructura de datos.

En general, hay muchas ocasiones en las que se puede crear un conjunto de DataSet dinámicamente sin tener un esquema disponible. En ese caso, el conjunto de datos es simplemente una estructura cómoda en la que se puede mantener la información, siempre y cuando los datos puedan representarse de forma relacional. Al mismo tiempo, puede aprovechar las capacidades del conjunto de datos, como la capacidad de serializar la información que se pasa a otro proceso o escribir un archivo XML.

## <a name="see-also"></a>Vea también

- [Herramientas de conjunto de datos](../data-tools/dataset-tools-in-visual-studio.md)