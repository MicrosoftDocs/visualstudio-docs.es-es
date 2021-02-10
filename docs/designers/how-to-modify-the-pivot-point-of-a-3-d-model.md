---
title: 'Cómo: Modificar el punto de pivote de un modelo en 3D'
description: Obtenga información sobre cómo usar el Editor de modelos para modificar el punto de pivote de un modelo 3D, que es el punto que define el centro del objeto para la rotación y el escalado.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c20b4ec8-29f5-4ca5-bc39-d4548ca6f573
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4eaa3d671a8c9aeb3ed942e57278160af73dec19
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99930842"
---
# <a name="how-to-modify-the-pivot-point-of-a-3d-model"></a>Cómo: Modificar el punto de pivote de un modelo en 3D

En este artículo se muestra cómo usar el Editor de modelos para modificar el *punto de pivote* de un modelo 3D. El punto de pivote es el punto en el espacio que define el centro matemático del objeto para la rotación y la escala.

## <a name="modify-the-pivot-point-of-a-3d-model"></a>Modificar el punto de pivote de un modelo en 3D

Puede volver a definir el origen de un modelo 3D modificando el punto de pivote.

Asegúrese de que se muestran la ventana **Propiedades** y el **Cuadro de herramientas**.

1. Comience con un modelo 3D existente, como el que se describe en [Cómo: Crear un modelo en 3D básico](../designers/how-to-create-a-basic-3-d-model.md).

2. Cambie al modo de pivote. En la barra de herramientas **Modo del Editor de modelos** haga clic en el botón **Modo de pivote** para activar este modo. Aparece un cuadro alrededor del botón **Modo de pivote** para indicar que el Editor de modelos está ahora en modo de pivote. En el modo de pivote, operaciones como la traslación afectan al punto de pivote del objeto en lugar de a la estructura del objeto en el espacio global.

3. Modifique el punto de pivote del objeto. En el modo **Seleccionar**, seleccione el objeto y, después, en la barra de herramientas del **Visor de modelos**, seleccione la herramienta **Trasladar**. Aparecerá un cuadro que representa el punto de pivote en la superficie de diseño. Mueva el cuadro para modificar el punto de pivote del objeto.

     Al mover el cuadro puede mover el punto de pivote en las tres dimensiones. Para trasladar el punto de pivote a lo largo de un eje, mueva la flecha que se corresponde a ese eje. El cuadro y las flechas cambiarán a un color amarillo para indicar el eje que se ve afectado por la traslación.

     También puede especificar el punto de pivote mediante la propiedad **Traslación de punto pivote** en la ventana **Propiedades**.

    > [!TIP]
    > Puede ver el efecto del nuevo punto de pivote girando el objeto. Para girarlo, use la herramienta **Girar** o modifique la propiedad **Rotación**.

Este es un modelo que tiene un punto de pivote modificado:

![Modelo de una casa que tiene un punto de pivote modificado](../designers/media/digit-modified-model.png)

## <a name="see-also"></a>Consulte también

- [Procedimiento: Crear un modelo en 3D básico](../designers/how-to-create-a-basic-3-d-model.md)
- [Editor de modelos](../designers/model-editor.md)
