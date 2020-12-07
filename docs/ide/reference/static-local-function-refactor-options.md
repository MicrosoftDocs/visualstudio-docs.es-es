---
title: Opciones de refactorización de funciones locales estáticas
description: Obtenga información sobre cómo usar el menú Acciones rápidas y refactorizaciones para convertir una función local en estática y pasar las variables definidas fuera de la función a la declaración y las llamadas de la función.
ms.custom: SEO-VS-2020
ms.date: 02/10/2020
ms.topic: reference
author: governesss
ms.author: midumont
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.make.local.function.static
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 8e85fcc96542b4f3538729aeb50a4e080c902657
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2020
ms.locfileid: "96479893"
---
# <a name="static-local-function-refactorings-and-quick-actions"></a>Refactorizaciones de la función local estática y acciones rápidas

En este artículo se describen dos características de productividad relacionadas con las funciones locales estáticas. Una es una refactorización que hace que una función local sea estática y la otra es una acción rápida que genera código para pasar variables a una función local estática.

## <a name="make-local-function-static"></a>Conversión de la función local en estática

Esta refactorización se aplica a lo siguiente:

- C#

**Qué:** Convierte una función local en estática y pasa las variables definidas fuera de la función a la declaración y llamadas de la función.

**Cuándo:** Quiere que la función local sea estática y que todas las variables se definan en el ámbito de la función.

**Por qué:** Las funciones locales estáticas mejoran la legibilidad: saber que el código específico está aislado facilita su comprensión, relectura y reutilización. Las funciones locales estáticas también proporcionan el ámbito para evitar contaminar una clase con una función estática que solo se llama en un método único.

### <a name="how-to"></a>Instrucciones

1. Coloque el símbolo de intercalación en el nombre de la función local.

2. Presione **Ctrl**+ **.** (punto) para activar el menú **Acciones rápidas y refactorizaciones**.

   ![Conversión de la función local en estática](media/make-local-function-static.png)

3. Seleccione **Convertir la función local "static"**.

## <a name="pass-variable-explicitly-in-a-static-local-function"></a>Paso de una variable explícitamente a una función local estática

Esta acción rápida se aplica a:

- C#

**Qué:** Pasa una variable explícitamente a una función estática local.

**Cuándo:** Quiere que una función local sea estática pero quiere seguir usando variables inicializadas fuera de ella.

**Por qué:** El uso de funciones locales estáticas proporciona aclaración a los lectores porque saben que solo se pueden declarar y llamar en un contexto específico del programa. Proporciona la flexibilidad para definir variables fuera de este contexto, pero aún puede pasarlas como argumentos a la función local estática.

### <a name="how-to"></a>Instrucciones

1. Coloque el símbolo de intercalación en la variable donde se usa la función local estática.

2. Presione **Ctrl**+ **.** (punto) para activar el menú **Acciones rápidas y refactorizaciones**.

   ![Paso de una variable explícitamente a una función local estática](media/pass-variable-explicitly-static-local-function.png)

3. Seleccione **Pass variable explicitly in local static function** (Pasar una variable explícitamente a una función estática local).

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)