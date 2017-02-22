---
title: "operadores de b&#250;squeda avanzada en expresiones de b&#250;squeda | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visor de Ayuda 2.0, buscar código"
  - "Visor de Ayuda 2.0, buscar código mediante el lenguaje de programación"
  - "Visor de Ayuda 2.0, buscar palabras clave"
  - "Visor de Ayuda 2.0, buscar títulos"
  - "buscar código [Visor de Ayuda 2.0]"
  - "buscar títulos [Visor de Ayuda 2.0]"
ms.assetid: 0cdc1746-8481-45ec-9c53-d0d89cdcbd5e
caps.latest.revision: 9
caps.handback.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# operadores de b&#250;squeda avanzada en expresiones de b&#250;squeda
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Utilice operadores de búsqueda avanzada para restringir la búsqueda de contenido mediante la creación de expresiones de búsqueda más complejas a partir de expresiones más sencillas.  Tal como muestra la tabla siguiente, estos operadores limitan el contexto en el que se ejecuta una consulta.  
  
> [!WARNING]
>  Para que el motor de búsqueda reconozca los operadores de búsqueda avanzada, estos deben tener un signo de dos puntos al final sin ningún espacio delante de los dos puntos.  
  
|Para buscar|Utilice|Ejemplo|Resultado|  
|-----------------|-------------|-------------|---------------|  
|Un término en el título del tema|título:|título:binaryreader|Temas que contienen “binaryreader” en los títulos.|  
|Un término en un ejemplo de código|código:|código:readdouble|Temas que contienen "readdouble" en un ejemplo de código.|  
|Un término en un ejemplo de un lenguaje de programación específico|código:vb:|código:vb:string|Temas que contienen “string” en un ejemplo de Visual Basic.|  
|Un tema asociado a una palabra clave de índice específica|palabra\_clave:|palabra\_clave:readbyte|Temas asociados a la palabra clave de índice “readbyte”.|  
  
 Puede utilizar el operador código: para buscar contenido sobre cualquiera de los distintos lenguajes de programación, pero este devuelve resultados únicamente para el contenido marcado para un lenguaje de programación específico.  En la tabla siguiente se enumeran los lenguajes de programación que admite este operador:  
  
|Lenguaje de programación|Utilice|  
|------------------------------|-------------|  
|Visual Basic|código:vb<br /><br /> o<br /><br /> código:visualbasic|  
|C\#|código:c\#<br /><br /> o<br /><br /> código:csharp|  
|C\+\+|código:cpp<br /><br /> o<br /><br /> código:C\+\+<br /><br /> o<br /><br /> código:cplusplus|  
|F\#|código:f\#<br /><br /> o<br /><br /> código:fsharp|  
|JavaScript|código:javascript<br /><br /> o<br /><br /> código:js|  
|XAML|código:xaml|  
  
## Vea también  
 [Operadores lógicos en expresiones de búsqueda](../ide/logical-operators-in-search-expressions.md)   
 [Sugerencias para la búsqueda de texto completo](../ide/full-text-search-tips.md)