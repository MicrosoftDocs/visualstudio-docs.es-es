---
title: Generación de una invalidación de método
description: Obtenga información sobre cómo generar inmediatamente el código para cualquier método que se puede invalidar desde una clase base.
ms.custom: SEO-VS-2020
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 3640fe29a18ba1ec89ab2806810165a0ec509167
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99968065"
---
# <a name="generate-an-override-in-visual-studio"></a>Generación de una invalidación en Visual Studio

Esta generación de código se aplica a:

- C#

- Visual Basic

**Qué:** Le permite generar inmediatamente el código para cualquier método que se puede invalidar en una clase base.

**Cuándo:** Desea reemplazar un método de clase base y generar la firma automáticamente.

**Por qué:** Podría escribir la firma del método manualmente; sin embargo, esta característica generará la firma automáticamente.

## <a name="how-to"></a>Instrucciones

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
