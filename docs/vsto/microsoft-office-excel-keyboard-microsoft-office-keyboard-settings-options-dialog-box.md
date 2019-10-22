---
title: Teclado de Office Excel, configuración de teclado, cuadro de diálogo Opciones
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ExcelOptions.KeyboardMappingScheme
- VS.ToolsOptionsPages.Microsoft_Office_Keyboard_Settings.Microsoft_Office_Excel_Keyboard
- VS.ToolsOptionsPages.Microsoft_Office_Tools.Microsoft_Office_Excel.Keyboard
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
ms.openlocfilehash: 090e943df2b61352c2342218c3c71c8f0e60eaad
ms.sourcegitcommit: cc5fd59e5dc99181601b7db8b28d7f8a83a36bab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2019
ms.locfileid: "66836033"
---
# <a name="microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box"></a>Cuadro de diálogo de opciones de teclado de Microsoft Office Excel, configuración de teclado de Microsoft Office
  Tanto Microsoft Office Excel y Visual Studio admiten el uso de teclas de método abreviado. La misma combinación de teclas de método abreviado puede corresponder a distintos comandos en Excel y en Visual Studio. Cuando Excel está abierto en un proyecto de nivel de documento en Visual Studio, sólo una aplicación a la vez recibe los comandos de teclas de método abreviado. De forma predeterminada, Visual Studio recibe todos los comandos de teclas de método abreviado, pero puede hacer que Excel recibirlos cuando el documento tiene el foco seleccionando **combinación de teclado dinámico**.

 Si usa una tecla de método abreviado que no está asignada a un comando en la aplicación que está controlando actualmente las teclas de método abreviado, la tecla de método abreviado se pasa a la otra aplicación.

 La opción que seleccione permanecerá en vigor para los proyectos de Excel hasta que la cambie. La selección no afecta a los proyectos de Microsoft Office Word. debe realizar cualquier cambio de Word mediante las opciones de teclado de Microsoft Office Word.

## <a name="uielement-list"></a>Lista de UIElement
 **Combinación de teclado de Visual Studio** Visual Studio recibe todos los comandos de teclas de método abreviado, incluso si Excel tiene el foco. Por ejemplo, si presiona la tecla de función **F5** mientras Excel tiene el foco, Visual Studio inicia la depuración de la solución.

 **Combinación de teclado dinámico** Visual Studio recibe los comandos de teclas de método abreviado sólo cuando tiene el foco. Cuando Excel tiene el foco, Excel recibe todos los comandos de teclas de método abreviado. Por ejemplo, si presiona la tecla de función **F5** mientras Excel tiene el foco, Excel se abre el **ir a** cuadro de diálogo. Si presiona **F5** mientras Visual Studio tiene el foco, Visual Studio inicia la depuración de la solución.

## <a name="see-also"></a>Vea también
- [Cuadro de diálogo de opciones de teclado de Microsoft Office Word, configuración de teclado de Microsoft Office](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)
