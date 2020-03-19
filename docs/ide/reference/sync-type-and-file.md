---
title: Cambio de un nombre de archivo para que coincida con un tipo
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 5b7a42a174fecd078e804f2ab3c35fbe442364a6
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594401"
---
# <a name="sync-a-type-to-a-filename-or-a-filename-to-a-type-refactoring"></a>Refactorización de sincronización de un tipo con un nombre de archivo o de un nombre de archivo con un tipo

Esta refactorización se aplica a lo siguiente:

- C#

- Visual Basic

**Qué:** Le permite cambiar el nombre de un tipo para que coincida con el nombre de archivo, o bien cambiar el nombre de un archivo para que coincida con el tipo que contiene.

**Cuándo:** Ha cambiado el nombre un archivo o un tipo y aún no ha actualizado aún el archivo o el tipo correspondiente para que coincidan.

**Por qué:** El hecho de colocar un tipo en un archivo con un nombre diferente, o viceversa, dificulta encontrar lo que está buscando. Al cambiar el nombre del tipo o del archivo, es más fácil leer el código y navegar hasta él.

> [!NOTE]
> Esta refactorización aún no está disponible para proyectos de .NET Standard y .NET Core.

## <a name="how-to"></a>Procedimiento

1. Resalte o coloque el cursor de texto en el nombre del tipo que se va a sincronizar:

   - C#:

       ![Código resaltado (C#)](media/synctype-highlight-cs.png)

   - Visual Basic:

       ![Código resaltado (Visual Basic)](media/synctype-highlight-vb.png)

2. A continuación, realice alguno de los siguientes procedimientos:

   - **Teclado**
      - Presione **Ctrl**+ **.** para activar el menú **Acciones rápidas y refactorizaciones** y seleccione **Cambiar nombre de archivo a *NombreTipo*.cs** en el menú emergente de la ventana Vista previa, donde *NombreTipo* es el nombre del tipo que ha seleccionado.
      - Presione **Ctrl**+ **.** para activar el menú **Acciones rápidas y refactorizaciones** y seleccione **Cambiar nombre de tipo a _NombreArchivo_.cs** en el menú emergente de la ventana Vista previa, donde *NombreArchivo* es el nombre del archivo actual.
   - **Mouse**
      - Haga clic con el botón derecho en el código, seleccione el menú **Acciones rápidas y refactorizaciones** y elija **Cambiar nombre de archivo a *NombreTipo*.cs** en el menú emergente de la ventana Vista previa, donde *NombreTipo* es el nombre del tipo que ha seleccionado.
      - Haga clic con el botón derecho en el código, seleccione el menú **Acciones rápidas y refactorizaciones** y elija **Cambiar nombre de tipo a _NombreArchivo_.cs** en el menú emergente de la ventana Vista previa, donde *NombreArchivo* es el nombre del archivo actual.

   El nombre del tipo o del archivo se cambia.

   - C#: En el siguiente ejemplo, el nombre de archivo **MyClass.cs** se ha cambiado a **MyNewClass.cs** para que coincida con el nombre de tipo.

       ![Resultado de la inserción (C#)](media/synctype-result-cs.png)

   - Visual Basic: En el siguiente ejemplo, el nombre de archivo **Employee.vb** se ha cambiado a **Person.vb** para que coincida con el nombre de tipo.

       ![Resultado de la inserción (Visual Basic)](media/synctype-result-vb.png)

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)
