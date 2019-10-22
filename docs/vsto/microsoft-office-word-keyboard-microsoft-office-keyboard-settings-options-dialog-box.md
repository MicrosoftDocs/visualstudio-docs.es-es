---
title: Teclado de Office Word, configuración de teclado, cuadro de diálogo Opciones
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Microsoft_Office_Tools.Microsoft_Office_Word.Keyboard
- VS.ToolsOptionsPages.Microsoft_Office_Keyboard_Settings.Microsoft_Office_Word_Keyboard
- VST.WordOptions.KeyboardMappingScheme
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- keyboard shortcuts, Office development in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5180aa2f4c5022cedcba2c5377d2ff2ac14ffb28
ms.sourcegitcommit: cc5fd59e5dc99181601b7db8b28d7f8a83a36bab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2019
ms.locfileid: "66835980"
---
# <a name="microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box"></a>Cuadro de diálogo de opciones de teclado de Microsoft Office Word, configuración de teclado de Microsoft Office
  Tanto Microsoft Office Word y Visual Studio admiten el uso de teclas de método abreviado. La misma combinación de teclas de método abreviado puede corresponder a distintos comandos en Word y en Visual Studio. Cuando Word está abierto en un proyecto de nivel de documento en Visual Studio, sólo una aplicación a la vez recibe los comandos de teclas de método abreviado. De forma predeterminada, Visual Studio recibe todos los comandos de teclas de método abreviado, pero puede hacer que Word recibirlos cuando el documento tiene el foco seleccionando **combinación de teclado dinámico**.

 Si usa una tecla de método abreviado que no está asignada a un comando en la aplicación que está controlando actualmente las teclas de método abreviado, la tecla de método abreviado se pasa a la otra aplicación.

 La opción que seleccione permanecerá en vigor para los proyectos de Word hasta que la cambie. La selección no afecta a los proyectos de Microsoft Office Excel. debe realizar los cambios en Excel mediante las opciones de teclado de Microsoft Office Excel.

## <a name="uielement-list"></a>Lista de UIElement
 **Combinación de teclado de Visual Studio** Visual Studio recibe todos los comandos de teclas de método abreviado, incluso si el documento de Word tiene el foco. Por ejemplo, si presiona la tecla de función **F5** mientras el documento tiene el foco, Visual Studio inicia la depuración de la solución.

 **Combinación de teclado dinámico** Visual Studio recibe los comandos de teclas de método abreviado sólo cuando tiene el foco. Cuando el documento de Word tiene el foco, Word recibe todos los comandos de teclas de método abreviado. Por ejemplo, si presiona la tecla de función **F5** mientras el documento de Word tiene el foco, se abre Word la **buscar y reemplazar** cuadro de diálogo con el **ir a** pestaña seleccionada. Si presiona **F5** mientras Visual Studio tiene el foco, Visual Studio inicia la depuración de la solución.

## <a name="see-also"></a>Vea también
- [Cuadro de diálogo de opciones de teclado de Microsoft Office Excel, configuración de teclado de Microsoft Office](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)
