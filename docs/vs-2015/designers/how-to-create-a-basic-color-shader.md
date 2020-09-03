---
title: 'Cómo: Crear un sombreador de color básico | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: c301328a-079a-49e8-b688-4749c01657c0
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 90f27e2359954e56a5b3d86bfc31883d4f29c44d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664585"
---
# <a name="how-to-create-a-basic-color-shader"></a>Cómo: Crear un sombreador de color básico
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este documento se muestra cómo usar el Diseñador de sombras y el lenguaje DGSL (Directed Graph Shader Language) para crear un sombreador de color plano. Este sombreador establece el color final en un valor de color RGB constante.

 Este documento muestra estas actividades:

- Quitar nodos de un gráfico

- Agregar nodos a un gráfico

- Establecer las propiedades del nodo

- Conectar nodos

## <a name="creating-a-flat-color-shader"></a>Crear a un sombreador de color plano
 Puede implementar un sombreador de color plano escribiendo el valor de color de una constante de color RGB en el color del resultado final.

 Antes de empezar, asegúrese de que se muestran la ventana **Propiedades** y el **Cuadro de herramientas**.

#### <a name="to-create-a-flat-color-shader"></a>Para crear a un sombreador de color plano

1. Cree un sombreador DGSL con el que trabajar. Para obtener información sobre cómo agregar un sombreador DGSL al proyecto, vea la sección Introducción de [Diseñador de sombras](../designers/shader-designer.md).

2. Elimine el nodo **Color de punto**. Use la herramienta **Seleccionar** para seleccionar el nodo **Color de punto** y, después, en la barra de menús, elija **Editar**, **Eliminar**.

3. Agregue un nodo **Constante de color** al gráfico. En el **Cuadro de herramientas**, en **Constantes**, seleccione **Constante de color** y muévala a la superficie de diseño.

4. Especifique un valor de color para el nodo **Constante de color**. Use la herramienta **Seleccionar** para seleccionar el nodo **Constante de color** y, después, en la ventana **Propiedades**, en la propiedad **Salida**, especifique un valor de color. Para el color naranja, especifique un valor de (1,0, 0,5, 0,2, 1,0).

5. Conecte la constante de color al color final. Para crear las conexiones, mueva el terminal **RGB** del nodo **Constante de color** al terminal **RGB** del nodo **Color final** y, después, mueva el terminal **Alfa** del nodo **Constante de color** al terminal **Alfa** del nodo **Color final**. Estas conexiones establecen el color final en la constante de color definida en el paso anterior.

   La ilustración siguiente muestra el gráfico de sombreador completo y una vista previa del sombreador aplicado a un cubo.

> [!NOTE]
> En la ilustración, el color naranja se especificó para ilustrar mejor el efecto del sombreador.

 ![Gráfico de sombreador y su resultado en un modelo de 3&#45;D](../designers/media/digit-flat-color-effect.png "Dígito-plano-color-efecto")

 Es posible que algunas formas proporcionen mejores vistas previas para algunos sombreadores. Para más información sobre cómo obtener una vista previa de los sombreadores en el Diseñador de sombras, vea [Diseñador de sombras](../designers/shader-designer.md).

## <a name="see-also"></a>Consulte también
 [Cómo: aplicar un sombreador a un modelo 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md) [Cómo: exportar un](../designers/how-to-export-a-shader.md) [sombreador sombreador](../designers/shader-designer.md) sombreador [nodos del diseñador](../designers/shader-designer-nodes.md) de sombras
