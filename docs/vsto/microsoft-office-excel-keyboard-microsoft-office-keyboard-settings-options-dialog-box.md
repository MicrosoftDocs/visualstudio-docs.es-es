---
title: Cuadro de diálogo de opciones de teclado de Microsoft Office Excel, configuración de teclado de Microsoft Office,
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: fc71c699dfea11b8654791efdd52e4c0751a9762
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34692452"
---
# <a name="microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box"></a>Cuadro de diálogo de opciones de teclado de Microsoft Office Excel, configuración de teclado de Microsoft Office,
  Tanto Microsoft Office Excel y Visual Studio admiten el uso de teclas de método abreviado. La misma combinación de teclas de método abreviado puede corresponder a distintos comandos en Excel y en Visual Studio. Cuando Excel está abierto en un proyecto de nivel de documento en Visual Studio, sólo una aplicación a la vez recibe los comandos de teclas de método abreviado. De forma predeterminada, Visual Studio recibe todos los comandos de teclas de método abreviado, pero puede hacer que Excel recibirlos cuando el documento tiene el foco seleccionando **combinación de teclado dinámico**.  
  
 Si utiliza una tecla de método abreviado que no está asignada a un comando en la aplicación que actualmente se está controlando las teclas de método abreviado, la tecla de método abreviado se pasa a la otra aplicación.  
  
 La opción que seleccione permanecerá en vigor para los proyectos de Excel hasta que la cambie. La selección no afecta a los proyectos de Microsoft Office Word. debe realizar cualquier cambio para Word utilizando las opciones de teclado de Microsoft Office Word.  
  
## <a name="uielement-list"></a>Lista de UIElement  
 **Combinación de teclado de Visual Studio**  
 Visual Studio recibe todos los comandos de teclas de método abreviado, incluso cuando Excel tiene el foco. Por ejemplo, si se presiona la tecla de función **F5** mientras Excel tiene el foco, Visual Studio inicia la depuración de la solución.  
  
 **Combinación de teclado dinámico**  
 Visual Studio recibe los comandos de teclas de método abreviado sólo cuando tiene el foco. Cuando Excel tiene el foco, Excel recibe todos los comandos de teclas de método abreviado. Por ejemplo, si se presiona la tecla de función **F5** mientras Excel tiene el foco, Excel se abre la **ir a** cuadro de diálogo. Si presiona **F5** mientras Visual Studio tiene el foco, Visual Studio inicia la depuración de la solución.  
  
## <a name="see-also"></a>Vea también  
 [Cuadro de diálogo de opciones de teclado de Microsoft Office Word, configuración de teclado de Microsoft Office,](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)  
  
  