---
title: Generación de una invalidación de método
ms.date: 01/26/2018
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 075c7dc49ffba1d67bbb5b62d313f50b5d09e956
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668445"
---
# <a name="generate-an-override-in-visual-studio"></a>Generación de una invalidación en Visual Studio

Esta generación de código se aplica a:

- C#

- Visual Basic

**Qué:** Permite generar inmediatamente el código para cualquier método que se puede invalidar en una clase base.

**Cuándo:** Se quiere reemplazar un método de clase base y generar la firma de forma automática.

**Por qué:** Se podría escribir la firma del método manualmente; pero esta característica generará la firma de forma automática.

## <a name="how-to"></a>Procedimiento

1. Escriba `override` (en C#) u `Overrides` (en Visual Basic), seguido de un espacio, donde quiera insertar un método de invalidación.

   - C#:

      ![Invalidación de IntelliSense (C#)](media/override-intellisense-cs.png)

   - Visual Basic:

      ![Invalidación de IntelliSense (VB)](media/override-intellisense-vb.png)

2. Seleccione el método que quiera invalidar de la clase base.

   > [!TIP]
   > - Use el icono de propiedad ![Icono de propiedad](media/override-property-cs.png) para mostrar u ocultar las propiedades en la lista.
   > - Use el icono de método ![Icono de método](media/override-method-cs.png) para mostrar u ocultar los métodos en la lista.

   La propiedad o el método seleccionado se agrega a la clase como una invalidación lista para implementarse.

   - C#:

       ![Resultado de la invalidación (C#)](media/override-result-cs.png)

   - Visual Basic:

       ![Resultado de la invalidación (VB)](media/override-result-vb.png)

## <a name="see-also"></a>Vea también

- [Generación de código](../code-generation-in-visual-studio.md)