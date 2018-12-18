---
title: Conjuntos de datos con tipo frente a conjuntos de datos sin tipo
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: c83ba0bb-5425-4d47-8891-6b4dbf937701
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: d817938a7611d7390e400cfbf69c6836b9256f3b
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/29/2018
ms.locfileid: "37117230"
---
# <a name="typed-vs-untyped-datasets"></a>Conjuntos de datos con tipo frente a conjuntos de datos sin tipo
Un conjunto de datos con tipo es un conjunto de datos que primero se deriva de la base de <xref:System.Data.DataSet> clase y, a continuación, usa información de la **Diseñador de Dataset**, que está almacenado en un archivo .xsd, para generar un nuevo establecimiento inflexible de tipos dataset (clase). La información del esquema (tablas, columnas etc.) se genera y compila en esta nueva clase de conjunto de datos como un conjunto de propiedades y objetos de primera clase. Dado que un dataset con tipo hereda de la base de <xref:System.Data.DataSet> (clase), la clase con tipo asume toda la funcionalidad de la <xref:System.Data.DataSet> clase y se puede usar con métodos que toman una instancia de un <xref:System.Data.DataSet> clase como parámetro.

 Un conjunto de datos sin tipo, en cambio, no tiene ningún esquema integrado correspondiente. Al igual que en un dataset con tipo, un conjunto de datos sin tipo contiene tablas, columnas y así sucesivamente, pero los que sólo se exponen como colecciones. (Sin embargo, después de crear manualmente las tablas y otros elementos de datos en un conjunto de datos sin tipo, puede exportar estructura del conjunto de datos como un esquema mediante el conjunto de datos <xref:System.Data.DataSet.WriteXmlSchema%2A> método.)

## <a name="contrast-data-access-in-typed-and-untyped-datasets"></a>Contraste acceso a los datos en conjuntos de datos con y sin tipo
 La clase para un conjunto de datos con tipo tiene un modelo de objetos en el que se toman sus propiedades en los nombres reales de las tablas y columnas. Por ejemplo, si está trabajando con un conjunto de datos con tipo, puede hacer referencia una columna mediante el uso de código como el siguiente:

 [!code-csharp[VbRaddataDatasets#4](../data-tools/codesnippet/CSharp/typed-vs-untyped-datasets_1.cs)]
 [!code-vb[VbRaddataDatasets#4](../data-tools/codesnippet/VisualBasic/typed-vs-untyped-datasets_1.vb)]

 En cambio, si está trabajando con un conjunto de datos sin tipo, el código equivalente es:

 [!code-csharp[VbRaddataDatasets#5](../data-tools/codesnippet/CSharp/typed-vs-untyped-datasets_2.cs)]
 [!code-vb[VbRaddataDatasets#5](../data-tools/codesnippet/VisualBasic/typed-vs-untyped-datasets_2.vb)]

 Acceso con tipo no sólo es más fácil de leer, pero también es totalmente compatible con IntelliSense en Visual Studio **Editor de código**. Además de ser más fácil trabajar con, la sintaxis del conjunto de datos con tipo proporciona comprobación de tipos en tiempo de compilación, reduce considerablemente la posibilidad de cometer errores al asignar valores a los miembros del conjunto de datos. Si cambia el nombre de una columna en su <xref:System.Data.DataSet> clase y, a continuación, compile la aplicación, recibirá un error de compilación. Haga doble clic en el error de compilación en el **lista de tareas**, puede ir directamente a la línea o líneas de código que haga referencia al nombre de columna antigua. Acceso a tablas y columnas en un conjunto de datos también es un poco más rápido en tiempo de ejecución porque el acceso se determina en tiempo de compilación, no a través de las colecciones en tiempo de ejecución.

 Aunque los conjuntos de datos con tipo tienen muchas ventajas, un conjunto de datos sin tipo resulta útil en una variedad de circunstancias. El escenario más evidente es cuando no hay ningún esquema disponible para el conjunto de datos. Esto puede ocurrir, por ejemplo, si la aplicación está interactuando con un componente que devuelve un conjunto de datos, pero no saber de antemano cuál es su estructura. De forma similar, hay veces cuando se trabaja con datos que no tienen una estructura estática y predecible. En ese caso, es práctico utilizar un conjunto de datos con tipo, ya que tendría que volver a generar la clase dataset con tipo con cada cambio realizado en la estructura de datos.

 Por lo general, hay muchas veces que se podría crear un conjunto de datos dinámicamente sin disponer de un esquema. En ese caso, el conjunto de datos es simplemente una estructura práctica en el que puede mantener información, como los datos se pueden representar de forma relacional. Al mismo tiempo, puede aprovechar las capacidades del conjunto de datos, como la capacidad de serializar la información para pasar a otro proceso o para escribir un archivo XML.

## <a name="see-also"></a>Vea también

- [Herramientas de conjunto de datos](../data-tools/dataset-tools-in-visual-studio.md)