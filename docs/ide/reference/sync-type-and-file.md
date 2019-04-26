---
title: Cambio de un nombre de archivo para que coincida con un tipo
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
ms.openlocfilehash: 90783dcd609094659517d994c3a4d4e0610b7735
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62945198"
---
# <a name="sync-a-type-to-a-filename-or-a-filename-to-a-type-refactoring"></a>Refactorización de sincronización de un tipo con un nombre de archivo o de un nombre de archivo con un tipo

Esta refactorización se aplica a lo siguiente:

- C#

- Visual Basic

**Qué:** Permite cambiar el nombre de un tipo para que coincida con el nombre de archivo, o bien cambiar el nombre de un archivo para que coincida con el tipo que contiene.

**Cuándo:** Se ha cambiado el nombre de un archivo o un tipo, y aún no se ha actualizado el archivo o el tipo correspondiente para que coincidan.

**Por qué:** La colocación de un tipo en un archivo con otro nombre, o viceversa, dificulta encontrar lo que se busca. Al cambiar el nombre del tipo o del archivo, es más fácil leer el código y navegar hasta él.

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
      - Presione **Ctrl**+**.** para activar el menú **Acciones rápidas y refactorizaciones** y seleccione **Cambiar nombre de archivo a *NombreTipo*.cs** en el menú emergente de la ventana Vista previa, donde *NombreTipo* es el nombre del tipo que ha seleccionado.
      - Presione **Ctrl**+**.** para activar el menú **Acciones rápidas y refactorizaciones** y seleccione **Cambiar nombre de tipo a _NombreArchivo_.cs** en el menú emergente de la ventana Vista previa, donde *NombreArchivo* es el nombre del archivo actual.
   - **Mouse**
      - Haga clic con el botón derecho en el código, seleccione el menú **Acciones rápidas y refactorizaciones** y elija **Cambiar nombre de archivo a *NombreTipo*.cs** en el menú emergente de la ventana Vista previa, donde *NombreTipo* es el nombre del tipo que ha seleccionado.
      - Haga clic con el botón derecho en el código, seleccione el menú **Acciones rápidas y refactorizaciones** y elija **Cambiar nombre de tipo a _NombreArchivo_.cs** en el menú emergente de la ventana Vista previa, donde *NombreArchivo* es el nombre del archivo actual.

   El nombre del tipo o del archivo se cambia.

   - C#: En el ejemplo siguiente, el nombre de archivo **MyClass.cs** se ha cambiado a **MyNewClass.cs** para que coincida con el nombre de tipo.

       ![Resultado de la inserción (C#)](media/synctype-result-cs.png)

   - Visual Basic: En el ejemplo siguiente, el nombre de archivo **Employee.vb** se ha cambiado a **Person.vb** para que coincida con el nombre de tipo.

       ![Resultado de la inserción (Visual Basic)](media/synctype-result-vb.png)

## <a name="see-also"></a>Vea también

- [Refactorización](../refactoring-in-visual-studio.md)
