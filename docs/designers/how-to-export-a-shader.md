---
title: "C&#243;mo: Exportar un sombreador | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0bd48bf4-9792-4456-a545-e462a2be668d
caps.latest.revision: 11
caps.handback.revision: 11
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
---
# C&#243;mo: Exportar un sombreador
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En este documento se muestra cómo usar el Diseñador de sombras para exportar un sombreador en lenguaje DGSL \(Directed Graph Shader Language\) para poder utilizarlo en una aplicación.  
  
 En este documento se muestra esta actividad:  
  
-   Exportar un sombreador  
  
## Exportar un sombreador  
 Después de crear un sombreador mediante el Diseñador de sombras y antes de que se pueda usar en la aplicación, tiene que exportarlo en un formato que entienda la API de los gráficos.  Puede exportar un sombreador de distintas maneras para satisfacer distintas necesidades.  
  
#### Para exportar un sombreador  
  
1.  En [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], abra un archivo de **Gráfico de sombreador visual \(.dgsl\)**.  
  
     Si no tiene un archivo de **Gráfico de sombreador visual \(.dgsl\)** que abrir, cree uno como se describe en [Cómo: Crear un sombreador de color básico](../designers/how-to-create-a-basic-color-shader.md).  
  
2.  En la barra de herramientas de **Diseñador de Presentación** , elija **opciones avanzadas**, **exportar**, **Exportar como**.  Aparecerá el cuadro de diálogo **Exportar sombreador**.  
  
3.  En la lista desplegable **Guardar como tipo**, elija el formato que desea exportar.  
  
     Estos son los formatos que puede elegir:  
  
     **Sombreador de píxeles de HLSL \(\*.hlsl\)**  
     Exporta el sombreador como código fuente de HLSL \(High Level Shader Language\).  Esta opción hace que sea posible modificar el sombreador más adelante, incluso después de implementarlo en una aplicación.  Esto puede facilitar la depuración y aplicación de revisiones al código basadas en problemas del usuario final, pero también permite que el usuario modifique el sombreador de forma no deseada, como por ejemplo, para obtener una ventaja injusta en un juego de competición.  También podría aumentar el tiempo de carga de presentación.  
  
     **Sombreador de píxeles compilados \(\*.cso\)**  
     Exporta el sombreador como código byte de HLSL.  Esta opción hace que sea posible modificar el sombreador más adelante, incluso después de implementarlo en una aplicación.  Esto puede facilitar la depuración y aplicación de revisiones al código basadas en problemas del usuario final, pero como el sombreador está precompilado, no produce una sobrecarga adicional de runtime cuando la aplicación carga el sombreador.  Los usuarios con suficientes conocimientos todavía pueden modificar el sombreador de formas no deseadas, pero la compilación del sombreador lo hace bastante más difícil.  
  
     **Encabezado de C\+\+ \(\*.h\)**  
     Exporta el sombreador como encabezado de estilo C que define una matriz de bytes que contiene el código byte de HLSL.  Esta opción puede hacer que se tarde más tiempo en depurar y aplicar revisiones al código basado en problemas del usuario final porque la aplicación se debe volver a compilar para probar la corrección.  Sin embargo, dado que esta opción lo dificulta, aunque no sea imposible, para modificar el sombreador después de que se haya implementado en una aplicación, se presenta la mayor dificultad para un usuario que desee modificar el sombreador de maneras innecesarias.  
  
4.  En el cuadro combinado **Nombre de archivo**, especifique un nombre para el sombreador exportado y, después, elija el botón **Guardar**.  
  
## Vea también  
 [Cómo: Crear un sombreador de color básico](../designers/how-to-create-a-basic-color-shader.md)   
 [Diseñador de sombras](../designers/shader-designer.md)