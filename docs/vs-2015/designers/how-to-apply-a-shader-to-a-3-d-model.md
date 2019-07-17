---
title: Procedimiento Aplicar un sombreador a un modelo 3D | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: a3877bd6-abd8-4a9d-842c-6848b6c2f335
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a55c1e71242e59c04066c09efa2375c4bafc485b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68156319"
---
# <a name="how-to-apply-a-shader-to-a-3-d-model"></a>Procedimiento Aplicación de un sombreador a un modelo 3D
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este documento se muestra cómo usar el Editor de modelos para aplicar un sombreador del lenguaje DGSL (Directed Graph Shader Language) a un modelo 3D.  
  
 Este documento muestra esta actividad:  
  
- Aplicar un sombreador a un modelo 3D  
  
## <a name="applying-a-shader-to-a-3-d-model"></a>Aplicar un sombreador a un modelo 3D  
 Puede aplicar un efecto de sombreador a un modelo 3D para darle un aspecto interesante.  
  
 Antes de empezar, asegúrese de que se muestra la ventana **Propiedades**.  
  
#### <a name="to-apply-a-shader-to-a-3-d-model"></a>Para aplicar un sombreador a un modelo 3D  
  
1. Comience con una escena 3D que contenga uno o varios modelos. Si no tienes una escena 3D adecuada, cree uno como se describe en [Cómo: Crear un modelo 3D básico](../designers/how-to-create-a-basic-3-d-model.md). También debe tener un sombreador DGSL que se pueda aplicar al modelo. Si no dispone de un sombreador adecuado, cree uno tal como se explica en [Cómo: Crear un sombreador de Color básico](../designers/how-to-create-a-basic-color-shader.md) y asegúrese de que se haya guardado en un archivo antes de continuar.  
  
2. En el modo **Seleccionar**, seleccione el modelo al que quiere aplicar el sombreador y, después, en la ventana **Propiedades**, en la propiedad **Nombre de archivo** del grupo de propiedades **Efecto**, especifique el sombreador DGSL que quiere aplicar al modelo.  
  
   Este es un modelo que tiene aplicado el efecto de color básico:  
  
   ![Escena 3D que muestra el efecto de color básico](../designers/media/digit-3d-model-effect.png "Digit-3D-Model-Effect")  
  
   Después de aplicar un sombreador a un modelo, puede abrirlo en el Diseñador de sombras si selecciona el modelo y, después, en la ventana **Propiedades**, en la propiedad **(Avanzadas)** del grupo de propiedades **Efecto**, pulsa el botón de puntos suspensivos ( **...** ).  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Crear un modelo 3D básico](../designers/how-to-create-a-basic-3-d-model.md)   
 [Cómo: Crear a un sombreador de Color básico](../designers/how-to-create-a-basic-color-shader.md)   
 [Editor de modelos](../designers/model-editor.md)   
 [Diseñador de sombras](../designers/shader-designer.md)
