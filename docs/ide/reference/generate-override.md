---
title: Generación de una invalidación de método
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 3c3a8f4eaf863fd8174ff70339fffc80141fc38d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "75569249"
---
# <a name="generate-an-override-in-visual-studio"></a>Generación de una invalidación en Visual Studio

Esta generación de código se aplica a:

- C#

- Visual Basic

**Qué:** Le permite generar inmediatamente el código para cualquier método que se puede invalidar en una clase base.

**Cuándo:** Desea reemplazar un método de clase base y generar la firma automáticamente.

**Por qué:** Podría escribir la firma del método manualmente; sin embargo, esta característica generará la firma automáticamente.

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
