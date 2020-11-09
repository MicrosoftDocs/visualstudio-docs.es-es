---
title: 'Cómo: Crear un sombreador de color básico'
description: Aprenda a usar el Diseñador de sombras y el lenguaje DGSL (Directed Graph Shader Language) para crear un sombreador de color plano que establezca el color final en un valor de color RGB constante.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c301328a-079a-49e8-b688-4749c01657c0
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d966a8fdc565eae5254d21dba4ab9dfaa440de94
ms.sourcegitcommit: a731a9454f1fa6bd9a18746d8d62fe2e85e5ddb1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2020
ms.locfileid: "93134111"
---
# <a name="how-to-create-a-basic-color-shader"></a>Cómo: Crear un sombreador de color básico

En este artículo se muestra cómo usar el Diseñador de sombras y el lenguaje DGSL (Directed Graph Shader Language) para crear un sombreador de color plano. Este sombreador establece el color final en un valor de color RGB constante.

## <a name="create-a-flat-color-shader"></a>Crear a un sombreador de color plano

Puede implementar un sombreador de color plano escribiendo el valor de color de una constante de color RGB en el color del resultado final.

Antes de empezar, asegúrese de que se muestran la ventana **Propiedades** y el **Cuadro de herramientas**.

1. Cree un sombreador DGSL con el que trabajar. Para obtener información sobre cómo agregar un sombreador DGSL al proyecto, vea la sección Introducción de [Diseñador de sombras](../designers/shader-designer.md).

2. Elimine el nodo **Color de punto**. Use la herramienta **Seleccionar** para seleccionar el nodo **Color de punto** y, después, en la barra de menús, elija **Editar** > **Eliminar**.

3. Agregue un nodo **Constante de color** al gráfico. En el **Cuadro de herramientas** , en **Constantes** , seleccione **Constante de color** y muévala a la superficie de diseño.

4. Especifique un valor de color para el nodo **Constante de color**. Use la herramienta **Seleccionar** para seleccionar el nodo **Constante de color** y, después, en la ventana **Propiedades** , en la propiedad **Salida** , especifique un valor de color. Para el color naranja, especifique un valor de (1,0, 0,5, 0,2, 1,0).

5. Conecte la constante de color al color final. Para crear las conexiones, mueva el terminal **RGB** del nodo **Constante de color** al terminal **RGB** del nodo **Color final** y, después, mueva el terminal **Alfa** del nodo **Constante de color** al terminal **Alfa** del nodo **Color final**. Estas conexiones establecen el color final en la constante de color definida en el paso anterior.

La ilustración siguiente muestra el gráfico de sombreador completo y una vista previa del sombreador aplicado a un cubo.

> [!NOTE]
> En la ilustración, el color naranja se especificó para ilustrar mejor el efecto del sombreador.

![Gráfico de sombreador y su resultado en un modelo 3D](../designers/media/digit-flat-color-effect.png)

Es posible que algunas formas proporcionen mejores vistas previas para algunos sombreadores. Para más información sobre cómo obtener una vista previa de los sombreadores en el Diseñador de sombras, vea [Diseñador de sombras](../designers/shader-designer.md).

## <a name="see-also"></a>Consulte también

- [Procedimiento: Aplicar un sombreador a un modelo en 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md)
- [Procedimiento: Exportar un sombreador](../designers/how-to-export-a-shader.md)
- [Diseñador de sombras](../designers/shader-designer.md)
- [Nodos del Diseñador de sombras](../designers/shader-designer-nodes.md)
