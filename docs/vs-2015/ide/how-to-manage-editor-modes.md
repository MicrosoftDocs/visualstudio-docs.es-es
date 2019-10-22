---
title: 'Cómo: Administrar los modos del editor | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- word wrap
- views, virtual space
- line numbers, displaying
- virtual space mode
- line numbers
- Code Editor, view and display options
- full screen mode
- Code Editor, modes
- views, splitting
- views, word wrapping
- fonts and size
- views, creating new windows
- views, line numbers
- views, changing mode
- views, outlining
ms.assetid: 1fb48027-d870-439f-8b72-4a0321390748
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a188e90d3feeb903eb8b4efceb91eb53cac3bdce
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651843"
---
# <a name="how-to-manage-editor-modes"></a>Cómo: Administrar los modos del editor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede mostrar el editor de Visual Studio Code en varios modos de visualización.

> [!NOTE]
> Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para obtener más información, vea [Personalizar la configuración de desarrollo en Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="enabling-full-screen-mode"></a>Habilitar el modo de pantalla completa
 Puede decidir ocultar todas las ventanas de herramientas y ver solo las ventanas de documento habilitando el modo **Pantalla completa**.

#### <a name="to-enable-full-screen-mode"></a>Para habilitar el modo de pantalla completa

- Presione ALT+MAYÚS+ENTRAR para entrar o salir del modo **Pantalla completa**.

     O bien

- Ejecute el comando `View.Fullscreen` en la ventana **Comandos**.

## <a name="enabling-virtual-space-mode"></a>Habilitar el modo de espacio virtual
 En el modo de **espacio virtual**, los espacios se insertan al final de cada línea de código. Seleccione esta opción para colocar los comentarios en una posición coherente al lado del código.

#### <a name="to-enable-virtual-space-mode"></a>Para habilitar el modo de espacio virtual

1. Seleccione **Opciones** en el menú **Herramientas**.

2. Expanda la carpeta **Editor de texto** y pulse **Todos los lenguajes** para establecer esta opción globalmente, o pulse una carpeta de lenguaje específica. (Por ejemplo, para activar los números de línea solo en Visual Basic, pulse las opciones Básico, Editor de texto).

3. Seleccione las opciones **General** y en **Configuración**, seleccione **Habilitar espacio virtual**.

    > [!NOTE]
    > **Espacio virtual** está habilitado en el modo **Selección de columnas**. Cuando el modo **Espacio virtual** no está habilitado, el punto de inserción se mueve desde el final de una línea directamente al primer carácter de la siguiente.

## <a name="see-also"></a>Vea también
 [Personalizar el editor](../ide/customizing-the-editor.md) [Cómo: organizar y acoplar](../misc/how-to-arrange-and-dock-windows.md) [fuentes y colores de Windows, entorno, opciones (cuadro de diálogo](../ide/reference/fonts-and-colors-environment-options-dialog-box.md) )
