---
title: Conversión de typeof en nameof
description: Obtenga información sobre cómo usar el menú Acciones rápidas y refactorizaciones de Visual Studio para convertir typeof en nameof en C# y GetType en NameOf en Visual Basic.
ms.date: 08/12/2020
ms.topic: reference
author: m-redding
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: f93c5232f852e1390eac9e2ebb57235abc5e1f6e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919696"
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
