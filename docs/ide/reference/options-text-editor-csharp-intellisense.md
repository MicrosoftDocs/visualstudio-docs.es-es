---
title: Opciones, editor de texto, C#, IntelliSense
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Intellisense
helpviewer_keywords:
- underlines, wavy
- IntelliSense [C#], options
- IntelliSense [C#], wavy underlines
- wavy underlines
- Text Editor Options dialog box, IntelliSense
ms.assetid: 3466dedb-e5f4-424c-8dd8-e4941b2f4fc2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 041b3c5d0a67d590bc409c21dd53d5d162b0a0b9
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/27/2018
ms.locfileid: "52389268"
---
# <a name="options-text-editor-c-intellisense"></a>Opciones, editor de texto, C#, IntelliSense

Use la página de opciones de **IntelliSense** para modificar la configuración que afecta al comportamiento de IntelliSense en C#. Para obtener acceso a esta página de opciones, elija **Herramientas** > **Opciones** y, después, elija **Editor de texto** > **C#** > **IntelliSense**.

La página de opciones de **IntelliSense** contiene las siguientes opciones:

## <a name="completion-lists"></a>Listas de finalización

- Mostrar lista de finalización después de escribir el carácter*

   Cuando esta opción está seleccionada, IntelliSense muestra automáticamente la lista de finalización cuando comienza a escribir. Cuando esta opción no está seleccionada, la finalización de IntelliSense sigue estando disponible desde el menú **IntelliSense** o presionando **Ctrl**+**Barra espaciadora**.

- Mostrar lista de finalización después de eliminar un carácter

- Resaltar partes coincidentes de elementos de la lista de finalización

- Mostrar filtros de elementos de finalización

## <a name="snippets-behavior"></a>Comportamiento de los fragmentos de código

- No incluir nunca fragmentos de código

   Cuando esta opción está seleccionada, IntelliSense nunca agrega a la lista de finalización alias relativos a los fragmentos de código de C#.

- Incluir siempre fragmentos de código

   Cuando esta opción está seleccionada, IntelliSense agrega alias para los fragmentos de código de C# a la lista de finalización. En el caso en que el alias de fragmento de código sea el mismo que una palabra clave, por ejemplo, [class](/dotnet/csharp/language-reference/keywords/class), la palabra clave se reemplaza mediante el acceso directo. Para obtener más información, vea [Fragmentos de código de C#](../../ide/visual-csharp-code-snippets.md).

- Incluir fragmentos de código cuando ?-Tab se escriba después de un identificador

   Si esta opción está seleccionada, IntelliSense agrega a la lista de finalización alias relativos a los fragmentos de código de C# cuando se presione **?**+**TAB** después de un identificador.

## <a name="enter-key-behavior"></a>Comportamiento de la tecla Entrar

- No agregar nunca una línea nueva al presionar Entrar

   Especifica que nunca se va a agregar una nueva línea automáticamente después de seleccionar un elemento en la lista de finalización y presionar **Entrar**.

- Agregar solo una nueva línea con Entrar al final de palabras

   Especifica que si escribe todos los caracteres de una entrada en la lista de finalización y, después, presiona **Entrar**, se crea una línea automáticamente y el cursor se mueve a esa nueva línea.

   Por ejemplo, si escribe `else` y, después, presiona **Entrar**, aparece lo siguiente en el editor:

   `else`

   `|` (ubicación del cursor)

   En cambio, si escribe solo `el` y, después, presiona **Entrar**, aparece lo siguiente en el editor:

   `else|` (ubicación del cursor)

- Agregar siempre una línea nueva al presionar Entrar

   Especifica que si escribe *cualquier* carácter de una entrada en la lista de finalización y, después, presiona **Entrar**, se crea una línea automáticamente y el cursor se mueve a esa nueva línea.

## <a name="show-name-suggestions"></a>Mostrar sugerencias de nombres

Finaliza automáticamente el nombre de objeto de los miembros que se han seleccionado recientemente.

## <a name="see-also"></a>Vea también

- [General, Entorno, Opciones (Cuadro de diálogo)](../../ide/reference/general-environment-options-dialog-box.md)
- [Usar IntelliSense](../../ide/using-intellisense.md)