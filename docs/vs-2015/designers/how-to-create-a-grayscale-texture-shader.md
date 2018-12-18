---
title: 'Cómo: Crear un sombreador de textura de escala de grises | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 79181d81-44af-445e-9a18-03483dd70260
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 046ae16670edaebb44986dee34ea086b4129a0a3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49922346"
---
# <a name="how-to-create-a-grayscale-texture-shader"></a>Cómo: Crear un sombreador de textura de escala de grises
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este documento se muestra cómo usar el Diseñador de sombras y el lenguaje DGSL (Directed Graph Shader Language) para crear un sombreador de textura de escala de grises. Este sombreador modifica el valor de color RGB del ejemplo de textura y después lo usa junto con el valor alfa sin modificar para establecer el color final.  
  
## <a name="creating-a-grayscale-texture-shader"></a>Crear un sombreador de textura de escala de grises  
 Puede implementar un sombreador de textura de escala de grises modificando el valor de color de una muestra de textura antes de escribirlo en el color de salida final.  
  
 Antes de empezar, asegúrese de que se muestran la ventana **Propiedades** y el **Cuadro de herramientas**.  
  
#### <a name="to-create-a-grayscale-texture-shader"></a>Para crear un sombreador de textura de escala de grises  
  
1. Cree un sombreador de textura básico, como se describe en [Cómo: Crear un sombreador de textura básico](../designers/how-to-create-a-basic-texture-shader.md).  
  
2. Desconecte el terminal **RGB** del nodo **Muestra de textura** del terminal **RGB** del nodo **Color final**. En el modo **Seleccionar**, elija el terminal **RGB** del nodo **Muestra de textura** y, después, elija **Romper vínculos**. Esto hace sitio para el nodo que se agrega en el paso siguiente.  
  
3. Agregue un nodo **Desaturar** al gráfico. En el **Cuadro de herramientas**, en **Filtros**, seleccione **Desaturar** y muévalo a la superficie de diseño.  
  
4. Calcule el valor de escala de grises mediante el nodo **Desaturar**. En el modo **Seleccionar**, mueva el terminal **RGB** del nodo **Muestra de textura** al terminal **RGB** del nodo **Desaturar**.  
  
   > [!NOTE]
   >  De forma predeterminada, el nodo **Desaturar** desatura completamente el color de entrada y usa las proporciones de luminancia estándar para la conversión de escala de grises. Puede cambiar el comportamiento del nodo **Desaturar** cambiando el valor de la propiedad **Luminancia** o solo desaturando parcialmente el color de entrada. Para desaturar parcialmente el color de entrada, proporcione un valor escalar en el intervalo [0,1) al terminal **Por ciento** del nodo **Desaturar**.  
  
5. Conecte el valor de color de escala de grises al color final. Mueva el terminal **Salida** del nodo **Desaturar** al terminal **RGB** del nodo **Color final**.  
  
   La ilustración siguiente muestra el gráfico de sombreador completo y una vista previa del sombreador aplicado a un cubo.  
  
> [!NOTE]
>  En esta ilustración, se usó un plano como la forma de vista previa y se especificó una textura para demostrar mejor el efecto del sombreador.  
  
 ![Gráfico de sombreador y vista previa de su efecto](../designers/media/digit-grayscale-effect.png "Digit-Grayscale-Effect")  
  
 Es posible que algunas formas proporcionen mejores vistas previas para algunos sombreadores. Para más información sobre cómo obtener una vista previa de los sombreadores en el Diseñador de sombras, vea [Diseñador de sombras](../designers/shader-designer.md)  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Aplicar un sombreador a un modelo 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md)   
 [Cómo: Exportar un sombreador](../designers/how-to-export-a-shader.md)   
 [Editor de imágenes](../designers/image-editor.md)   
 [Diseñador de sombras](../designers/shader-designer.md)   
 [Nodos del Diseñador de sombras](../designers/shader-designer-nodes.md)



