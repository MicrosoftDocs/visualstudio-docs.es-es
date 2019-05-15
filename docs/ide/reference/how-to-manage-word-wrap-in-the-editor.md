---
title: Ajuste de línea
ms.date: 11/07/2018
ms.topic: conceptual
helpviewer_keywords:
- word wrap
- editors, text viewing
- Code Editor, word wrap
ms.assetid: 442f33ef-9f52-4515-b55f-fb816d664645
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 02ef55b44d57cecadb690637c17c0a35e9cb0659
ms.sourcegitcommit: 614d5b99576ea27a41957cd94062dc95cbd29c1c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/10/2019
ms.locfileid: "65531615"
---
# <a name="how-to-manage-word-wrap-in-the-editor"></a>Procedimiento Administrar el ajuste de línea en el editor

Puede establecer y desactivar la opción **Ajuste automático de línea**. Cuando se establece esta opción, se muestra la parte de una línea larga que se extiende más allá del ancho actual de la ventana del editor de código en la siguiente línea. Cuando se desactiva esta opción, por ejemplo, para facilitar el uso de numeración de líneas, puede desplazarse a la derecha para ver los finales de las líneas largas.

> [!NOTE]
> Este tema solo se aplica a Visual Studio para Windows. Visual Studio para Mac no admite de momento el ajuste de línea.

## <a name="to-set-word-wrap-preferences"></a>Para establecer las preferencias de ajuste automático de línea

1. En el menú **Herramientas**, seleccione **Opciones**.

2. En la carpeta **Editor de texto**, pulse las opciones **General** en la subcarpeta **Todos los lenguajes** para establecer esta opción globalmente.

     o

     Pulse las opciones **General** en la subcarpeta del lenguaje en el que está programando.

3. En **Configuración**, seleccione o desactive la opción **Ajuste automático de línea**.

     Cuando la opción **Ajuste automático de línea** está seleccionada, la opción **Mostrar glifos visuales para ajuste de línea** está habilitada.

4. Seleccione la opción **Mostrar glifos visuales para ajuste de línea** si prefiere mostrar un indicador de flecha de retorno donde una línea larga se ajusta en una segunda línea. Desactive esta opción si prefiere no mostrar indicadores de flecha.

    > [!NOTE]
    > Estas flechas de aviso no se agregan a su código, sino que solo se usan para fines de visualización.

## <a name="known-issues"></a>Problemas conocidos

Si está familiarizado con el ajuste de línea en Notepad++, Sublime Text o Visual Studio Code, tenga en cuenta los siguientes problemas donde Visual Studio se comporta de forma diferente a otros editores:

* [No se selecciona toda la línea al hacer triple clic](https://developercommunity.visualstudio.com/content/problem/268989/triple-click-doesnt-select-whole-line-when-word-wr.html)
* [El comando Cortar no elimina toda la línea](https://developercommunity.visualstudio.com/content/problem/138259/cut-command-should-delete-logical-line.html)
* [Al presionar la tecla Fin dos veces no se mueve el cursor al final de la línea](https://developercommunity.visualstudio.com/content/problem/138274/pressing-end-key-twice-should-move-cursor-to-end-o.html)

## <a name="see-also"></a>Vea también

- [Editor de texto, Opciones (cuadro de diálogo)](../../ide/reference/text-editor-options-dialog-box.md)
- [Características del editor de código](../../ide/writing-code-in-the-code-and-text-editor.md)
