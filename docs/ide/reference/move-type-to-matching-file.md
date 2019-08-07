---
title: Refactorización de traslado de un tipo a un archivo coincidente
description: Mueva un tipo a un archivo independiente con el mismo nombre. Haga clic con el botón derecho en el tipo, seleccione Acciones rápidas y refactorizaciones y elija Mover tipo a <TypeName>.cs.
ms.date: 01/26/2018
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 3021e08d3cfb601a67f51e53c97d2eba60c397a5
ms.sourcegitcommit: 0f5f7955076238742f2071d286ad8e896f3a6cad
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/25/2019
ms.locfileid: "68483654"
---
# <a name="move-a-type-to-a-matching-file-refactoring"></a>Refactorización de traslado de un tipo a un archivo coincidente

Esta refactorización se aplica a lo siguiente:

- C#

- Visual Basic

**Qué:** Permite mover el tipo seleccionado a un archivo independiente con el mismo nombre.

**Cuándo:** Hay varias clases, estructuras, interfaces, etc. en el mismo archivo que se quieren separar.

**Por qué:** La colocación de varios tipos en el mismo archivo puede dificultar su búsqueda. Al trasladar los tipos a archivos con el mismo nombre, es más fácil leer el código y navegar hasta él.

## <a name="how-to"></a>Procedimiento

1. Coloque el cursor dentro del nombre del tipo donde está definido. Por ejemplo:

   ```csharp
   class Person
   ```

   ```vb
   Class Person
   ```

2. A continuación, realice alguno de los siguientes procedimientos:

   - Presione **Ctrl**+ **.**
   - Haga clic con el botón derecho en el nombre del tipo y seleccione **Acciones rápidas y refactorizaciones**

1. Seleccione **Mover tipo a *TypeName*.cs** desde el menú, donde *TypeName* es el nombre del tipo que seleccionó.

   El tipo se mueve a un archivo nuevo en el proyecto con el mismo nombre del tipo.

   - C#:

      ![Resultado de la inserción (C#)](media/movetype-result-cs.png)

   - Visual Basic:

      ![Resultado de la inserción (Visual Basic)](media/movetype-result-vb.png)

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)
