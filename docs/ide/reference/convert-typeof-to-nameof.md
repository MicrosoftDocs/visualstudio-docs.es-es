---
title: Conversión de typeof en nameof
description: Obtenga información sobre cómo usar el menú Acciones rápidas y refactorizaciones de Visual Studio para convertir typeof en nameof en C# y GetType en NameOf en Visual Basic.
ms.date: 08/12/2020
ms.topic: reference
author: m-redding
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: ce76b82e2ebc68634be7cf4d463f6b8216d81e06
ms.sourcegitcommit: 3c571f44bfd6402efea5187af43df287bac5b6ac
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/24/2020
ms.locfileid: "97761204"
---
# <a name="convert-typeof-to-nameof"></a>Convertir `typeof` en `nameof`

Esta refactorización se aplica a lo siguiente:

- C#
- Visual Basic

**Qué:** Permite convertir una instancia de `typeof(<QualifiedType>).Name` en `nameof(<QualifiedType>)` en C# y una instancia de `GetType(<QualifiedType>).Name` en `NameOf(<QualifiedType>)` en Visual Basic.

**Cuándo:**  Todas las instancias de `typeof(<QualifiedType>).Name` donde `someType` no es un tipo genérico. Esta exclusión es necesaria porque este caso no devuelve el mismo valor de cadena que `nameof(<QualifiedType>)`. Lo mismo se aplica a la instancia de Visual Basic.

**Por qué:** Al usar `nameof` en lugar del nombre de `type`, se evita la reflexión implicada en la recuperación de un objeto `type`, y es una forma más pragmática de escribirlo.

## <a name="how-to"></a>Instrucciones

1. Coloque el cursor dentro de la instancia de `typeof(<QualifiedType>).Name` para C# o `GetType(<QualifiedType>).Name` en Visual Basic.

2. Presione **Ctrl**+ **.** para activar el menú **Acciones rápidas y refactorizaciones**.

3. Seleccione una de las opciones siguientes:

    - C#
      <br>Seleccione **Convertir "typeof" en "nameof"** : ![Captura de pantalla en la que se muestran el menú Acciones rápidas y refactorizaciones de Visual Studio con la opción "Convert 'typeof' to 'nameof'" (Convertir "typeof" en "nameof") seleccionada, y cambios en el código de C#.](media/convert-type-of.PNG)

    - Visual Basic
      <br>Seleccione **Convertir "GetType" en "NameOf"** : ![Captura de pantalla en la que se muestran el menú Acciones rápidas y refactorizaciones de Visual Studio con la opción "Convert 'GetType' to 'NameOf'" (Convertir "GetType" en "NameOf") seleccionada, y cambios en el código de Visual Basic.](media/convert-get-type.PNG)

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)
