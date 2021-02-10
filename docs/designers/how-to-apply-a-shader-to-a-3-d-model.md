---
title: 'Cómo: Aplicar un sombreador a un modelo en 3D'
description: Aprenda a usar el Editor de modelos para aplicar un sombreador de lenguaje DGSL (Directed Graph Shader Language) a un modelo 3D para darle un aspecto interesante.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: a3877bd6-abd8-4a9d-842c-6848b6c2f335
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bdaf4b86bfc773df678c03875a9ec260cd72084f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917076"
---
# <a name="how-to-apply-a-shader-to-a-3d-model"></a>Cómo: Aplicar un sombreador a un modelo en 3D

En este artículo se muestra cómo usar el Editor de modelos para aplicar un sombreador del lenguaje DGSL (Directed Graph Shader Language) a un modelo 3D.

## <a name="apply-a-shader-to-a-3d-model"></a>Aplicar un sombreador a un modelo en 3D

Puede aplicar un efecto de sombreador a un modelo 3D para darle un aspecto interesante.

Antes de empezar, asegúrese de que se muestra la ventana **Propiedades**.

1. Comience con una escena 3D que contenga uno o varios modelos. Si no dispone de una escena 3D adecuada, cree una tal como se explica en [Cómo: Crear un modelo en 3D básico](../designers/how-to-create-a-basic-3-d-model.md). También debe tener un sombreador DGSL que se pueda aplicar al modelo. Si no dispone de un sombreador adecuado, cree uno como se describe en [Cómo: Crear un sombreador de color básico](../designers/how-to-create-a-basic-color-shader.md) y asegúrese de guardarlo en un archivo antes de continuar.

2. En el modo **Seleccionar**, seleccione el modelo al que quiere aplicar el sombreador y, después, en la ventana **Propiedades**, en la propiedad **Nombre de archivo** del grupo de propiedades **Efecto**, especifique el sombreador DGSL que quiere aplicar al modelo.

Este es un modelo que tiene aplicado el efecto de color básico:

![Escena 3D que muestra el efecto de color básico](../designers/media/digit-3d-model-effect.png)

Después de aplicar un sombreador a un modelo, puede abrirlo en el Diseñador de sombras si selecciona el modelo y, después, en la ventana **Propiedades**, en la propiedad **(Avanzadas)** del grupo de propiedades **Efecto**, pulsa el botón de puntos suspensivos (**...**).

## <a name="see-also"></a>Consulte también

- [Procedimiento: Crear un modelo en 3D básico](../designers/how-to-create-a-basic-3-d-model.md)
- [Procedimiento: Crear un sombreador de color básico](../designers/how-to-create-a-basic-color-shader.md)
- [Editor de modelos](../designers/model-editor.md)
- [Diseñador de sombras](../designers/shader-designer.md)
