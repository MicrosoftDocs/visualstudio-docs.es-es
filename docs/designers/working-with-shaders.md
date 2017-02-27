---
title: "Trabajar con sombreadores | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6b2ea1ed-b995-4e75-af19-c68fd37a3bc5
caps.latest.revision: 8
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
caps.handback.revision: 8
---
# Trabajar con sombreadores
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede utilizar el Diseñador de sombras basado en gráficos de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para diseñar efectos de sombreador personalizados.  Puede utilizar estos sombreadores en su juego o aplicación basado en DirectX.  
  
## Sombreadores  
 Un *sombreador* es un programa informático que realiza cálculos gráficos, por ejemplo, transformaciones de vértices o coloreado de píxeles, y se ejecuta normalmente en una unidad central de gráficos \(GPU\) en lugar de en una CPU.  Dado que la mayoría de las fases de la canalización de gráficos tradicional de función fija se realizan ahora mediante programas del sombreador, puede usarlas para crear una canalización específica para las necesidades de su aplicación.  
  
 Los tipos más comunes de sombreadores son los *sombreadores de vértices*, que realizan cálculos por vértices y reemplazan al conjunto de circuitos de iluminación y transformación de función fija en el hardware de gráficos no programable, y los *sombreadores de píxeles*, que realizan cálculos por píxel que determinan el color de un píxel y reemplazan al conjunto de circuitos de combinación de colores de función fija en el hardware de gráficos no programable.  El hardware de gráficos moderno ha creado incluso más clases posibles de sombreadores: *sombreadores de casco*, *sombreadores de dominio* y *sombreadores de geometría* para los cálculos de gráficos y *sombreadores de cálculo* para los cálculos que no son gráficos.  Ninguna de estas fases se encuentran disponibles en hardware no programable de gráficos.  Los sombreadores se crearon originalmente mediante un lenguaje similar al ensamblador que proporcionaba instrucciones paralelas de datos \(SIMD\) y orientadas a gráficos \(producto de puntos\)  Ahora, los sombreadores se crean por lo general usando lenguajes tipo C de alto nivel como HLSL \(High Level Shader Language\).  
  
 Puede utilizar el Diseñador de sombras para crear sombreadores de píxeles interactivamente en lugar de escribir y compilar código.  En el Diseñador de sombras, se define un sombreador mediante varios nodos que representan datos y operaciones y conexiones entre nodos que representan el flujo de valores de datos y los resultados intermedios a través del sombreador.  Al usar este enfoque y la vista previa en tiempo real en el Diseñador de sombras, puede visualizar la ejecución del sombreador más fácilmente, y “detectar” variaciones interesantes del sombreador mediante la experimentación.  
  
## DGSL, documentos  
 El Diseñador de sombras guarda los sombreadores en el formato DGSL \(Directed Graph Shader Language\), que es un formato XML basado en el lenguaje DGML \(Directed Graph Markup Language\).  Puede aplicar sombreadores de DGSL directamente a los modelos 3D en el Editor de modelos.  Sin embargo, para poder usar un sombreador de DGSL en su aplicación, debe exportarlo a un formato que DirectX comprenda, por ejemplo, HLSL.  
  
 Dado que DGSL es compatible con DGML, puede usar las herramientas diseñadas para analizar documentos DGML para analizar los sombreadores de DGSL.  Para obtener información sobre DGML, vea [Lenguaje de marcado dirigido de introducción \(DGML\) de Gráficos](http://msdn.microsoft.com/library/ee842619.aspx).  
  
## Temas relacionados  
  
|Título|Descripción|  
|------------|-----------------|  
|[Diseñador de sombras](../designers/shader-designer.md)|Describe cómo usar el diseñador de sombras de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para operar con sombreadores.|  
|[Nodos del Diseñador de sombras](../designers/shader-designer-nodes.md)|Describe las clases de nodos del Diseñador de sombras que puede usar para lograr efectos gráficos.|  
|[Ejemplos del Diseñador de sombras](../designers/shader-designer-examples.md)|Proporciona vínculos a temas que muestran cómo usar el Diseñador de sombras para lograr efectos comunes en los gráficos.|