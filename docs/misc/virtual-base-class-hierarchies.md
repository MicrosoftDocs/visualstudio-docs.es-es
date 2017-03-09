---
title: "Jerarqu&#237;as de clases base virtuales | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "clases [C++], clases base virtuales"
  - "jerarquías de clases, clases base virtuales"
  - "clases derivadas, consideraciones de la jerarquía de clases"
  - "funciones virtuales, en jerarquías de clases base virtuales"
  - "clases base virtuales"
  - "clases base virtuales, jerarquías"
  - "jerarquías de clases base virtuales"
ms.assetid: d24fda17-f829-48d6-84ec-8100f26bc5cf
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Jerarqu&#237;as de clases base virtuales
Algunas jerarquías de clases son amplias pero tienen muchas cosas en común. El código común se implementa en una clase base, mientras que el código concreto está en clases derivadas.  
  
 Es importante que las clases base establezcan un protocolo mediante el cual las clases derivadas puedan alcanzar la máxima funcionalidad. Estos protocolos se implementan normalmente mediante funciones virtuales. En ocasiones, la clase base proporciona una implementación predeterminada para tales funciones. En una jerarquía de clases tal como la jerarquía `Document` de la ilustración Ejemplo de gráfico acíclico dirigido \(vea [Herencia simple](/visual-cpp/cpp/single-inheritance)\), dos funciones útiles son `Identify` y `WhereIs`.  
  
 Cuando recibe una llamada, la función `Identify` devuelve un identificador correcto, adecuado para la clase de documento: para `Book`, una llamada de función tal como `doc->Identify()` debe devolver el número ISBN; sin embargo, para `HelpFile`, un nombre de producto y un número de revisión probablemente sean más adecuados. De igual forma, `WhereIs` debe devolver una fila y un estante para `Book`, pero para `HelpFile` debe devolver una ubicación de disco, quizá un directorio y un nombre de archivo.  
  
 Es importante que todas las implementaciones de las funciones `Identify` y `WhereIs` devuelvan el mismo tipo de información. En este caso, una cadena de caracteres es lo adecuado.  
  
 Estas funciones se implementan como funciones virtuales y, a continuación, se invocan mediante un puntero a una clase base. El enlace al código real se produce en tiempo de ejecución, seleccionando la función `Identify` o `WhereIs` correcta.  
  
## Vea también  
 [Información general de las clases derivadas](../misc/overview-of-derived-classes.md)