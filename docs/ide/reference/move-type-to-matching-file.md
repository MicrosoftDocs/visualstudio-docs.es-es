---
title: Traslado de un tipo a una refactorización de archivo coincidente en Visual Studio
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 73e1d9d67d905fed5eb37e29c1be1ba7677da3e8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49884154"
---
# <a name="move-a-type-to-a-matching-file-refactoring"></a>Refactorización de traslado de un tipo a un archivo coincidente

Esta refactorización se aplica a lo siguiente:

- C#

- Visual Basic

**Qué:** Le permite mover el tipo seleccionado a un archivo independiente con el mismo nombre.

**Cuándo:** Tiene varias clases, estructuras, interfaces, etc. en el mismo archivo que desea separar.

**Por qué:** Colocar varios tipos en el mismo archivo puede dificultar su búsqueda. Al trasladar los tipos a archivos con el mismo nombre, es más fácil leer el código y navegar hasta él.

## <a name="how-to"></a>Procedimiento

1. Coloque el cursor dentro del nombre del tipo donde está definido. Por ejemplo:

   ```csharp
   class Person
   ```

   ```vb
   Class Person
   ```

2. A continuación, realice alguno de los siguientes procedimientos:

   - Presione **Ctrl**+**.**
   - Haga clic con el botón derecho en el nombre del tipo y seleccione **Acciones rápidas y refactorizaciones**

1. Seleccione **Mover tipo a *TypeName*.cs** desde el menú, donde *TypeName* es el nombre del tipo que seleccionó.

   El tipo se mueve a un archivo nuevo en el proyecto con el mismo nombre del tipo.

   - C#:

      ![Resultado de la inserción (C#)](media/movetype-result-cs.png)

   - Visual Basic:

      ![Resultado de la inserción (Visual Basic)](media/movetype-result-vb.png)

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)
