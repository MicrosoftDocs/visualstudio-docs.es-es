---
title: "Generación de una invalidación de método en Visual Studio | Documentos de Microsoft"
ms.custom: 
ms.date: 01/26/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: df0eecdeb2aad15e1da68cef3b125c3c95f57e78
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
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

1. Seleccione el método que quiera invalidar de la clase base.

   > [!TIP]
   > - Use el icono de propiedad ![Icono de propiedad](media/override-property-cs.png) para mostrar u ocultar las propiedades en la lista.
   > - Use el icono de método ![Icono de método](media/override-method-cs.png) para mostrar u ocultar los métodos en la lista.

   La propiedad o el método seleccionado se agrega a la clase como una invalidación lista para implementarse.

   - C#:

      ![Resultado de la invalidación (C#)](media/override-result-cs.png)

   - Visual Basic:

      ![Resultado de la invalidación (VB)](media/override-result-vb.png)

## <a name="see-also"></a>Vea también

[Generación de código](../code-generation-in-visual-studio.md)
