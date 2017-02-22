---
title: "C&#243;mo: Aplicar un sombreador a un modelo 3D | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a3877bd6-abd8-4a9d-842c-6848b6c2f335
caps.latest.revision: 15
caps.handback.revision: 15
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
---
# C&#243;mo: Aplicar un sombreador a un modelo 3D
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En este documento se muestra cómo utilizar el editor del modelo para aplicar un sombreador de \(DGSL\) de lenguaje de Directed Graph query language Sombreador un modelo 3D.  
  
 En este documento se muestra esta actividad:  
  
-   Aplicar un sombreador a un modelo 3D  
  
## Aplicar un sombreador a un modelo 3D  
 Puede aplicar un efecto de sombreador a un modelo 3D para darle un aspecto interesante.  
  
 Antes de empezar, asegúrese de que la ventana de **Propiedades** está visible.  
  
#### Para aplicar un sombreador a un modelo 3D  
  
1.  Comience con una escena 3D que contiene uno o más modelos.  Si no tiene una escena 3D conveniente, cree uno como se describe en [Cómo: Crear un modelo 3D básico](../designers/how-to-create-a-basic-3-d-model.md).  También tiene que tener un sombreador de DGSL que puede aplicar al modelo.  Si no tiene un sombreador conveniente, cree uno como se describe en [Cómo: Crear un sombreador de color básico](../designers/how-to-create-a-basic-color-shader.md) y asegúrese de que se ha guardado en un archivo antes de continuar.  
  
2.  En el modo de **activada** , seleccione el modelo al que desea aplicar el sombreador y, en la ventana de **Propiedades** , en la propiedad de **Nombre de archivo** de grupo de propiedades de **Efecto** , especifique el sombreador de DGSL que desea aplicar al modelo.  
  
 A continuación se muestra un modelo que tiene el efecto de color básico aplicado al:  
  
 ![Escena 3D que muestra el efecto de color básico](../designers/media/digit-3d-model-effect.png "Digit\-3D\-Model\-Effect")  
  
 Después de aplicar un sombreador a un modelo, puede abrirlo en el Sombreador Diseñador seleccionando el modelo y, en la ventana de **Propiedades** , en la propiedad de **\(Avanzado\)** de grupo de propiedades de **Efecto** , elija el botón de puntos suspensivos \(**...**\).  
  
## Vea también  
 [Cómo: Crear un modelo 3D básico](../designers/how-to-create-a-basic-3-d-model.md)   
 [Cómo: Crear un sombreador de color básico](../designers/how-to-create-a-basic-color-shader.md)   
 [Editor de modelos](../designers/model-editor.md)   
 [Diseñador de sombras](../designers/shader-designer.md)