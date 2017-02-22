---
title: "Operadores l&#243;gicos en expresiones de b&#250;squeda | Microsoft Docs"
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
  - "Visor de la Ayuda 2.0, operadores lógicos en la búsqueda"
  - "operadores lógicos en la búsqueda [Visor de Ayuda 2.0]"
ms.assetid: 0c38ae7d-3e20-4d47-a020-9677cd285916
caps.latest.revision: 9
caps.handback.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Operadores l&#243;gicos en expresiones de b&#250;squeda
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Utilice operadores lógicos para restringir la búsqueda de contenido mediante la creación de expresiones de búsqueda más complejas a partir de expresiones más sencillas.  Tal como muestra la tabla siguiente, los operadores lógicos especifican cómo se deben combinar varios términos de búsqueda en una consulta de búsqueda.  
  
> [!IMPORTANT]
>  Debe escribir los operadores lógicos con todas las letras en mayúsculas para que el motor de búsqueda los reconozca.  
  
|Para buscar|Utilice|Ejemplo|Resultado|  
|-----------------|-------------|-------------|---------------|  
|Ambos términos en el mismo tema|AND|dib AND palette|Temas que contienen "dib" y "palette".|  
|Cualquier término en un tema|OR|trama OR vector|Temas que contienen "trama" o "vector".|  
|El primer término sin el segundo en el mismo tema|NOT|"sistema operativo" NOT DOS|Temas que contienen "sistema operativo", pero no "DOS".|  
|Ambos términos muy próximos en un tema|NEAR|usuario NEAR kernel|Temas que contienen "usuario" cerca de "kernel".|  
  
## Vea también  
 [Sugerencias para la búsqueda de texto completo](../ide/full-text-search-tips.md)   
 [Encontrar información](../ide/locate-information.md)