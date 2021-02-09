---
title: Teclado de Office Excel, configuración, opciones (cuadro de diálogo)
description: Obtenga información acerca de cómo puede hacer que Microsoft Excel reciba comandos de tecla de método abreviado cuando el documento tiene el foco seleccionando esquema de teclado dinámico.
ms.custom: SEO-VS-2020
titleSuffix: ''
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 914b86e6e2b27d18e2089d44ce97810f82294c5e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99880351"
---
# <a name="microsoft-office-excel-keyboard-settings-options-dialog-box"></a>Microsoft Office teclado, configuración, opciones (cuadro de diálogo) de Excel
  Microsoft Office Excel y Visual Studio controlan las teclas de método abreviado. La misma combinación de teclas de método abreviado puede tener distintos comandos en Excel y en Visual Studio. Cuando Excel está abierto en un proyecto de nivel de documento en Visual Studio, solo una aplicación a la vez recibe los comandos de tecla de método abreviado. De forma predeterminada, Visual Studio recibe todos los comandos de teclas de método abreviado, pero puede hacer que Excel los reciba cuando el documento tenga el foco seleccionando **esquema de teclado dinámico**.

 Si usa una tecla de método abreviado que no está asignada a un comando en la aplicación que está controlando las teclas de método abreviado, la tecla de método abreviado se pasa a la otra aplicación.

 La opción que seleccione permanecerá en vigor para los proyectos de Excel hasta que la cambie. La selección no afecta a Microsoft Office proyectos de Word; debe hacer cualquier cambio en Word con las opciones de teclado de Word Microsoft Office.

## <a name="uielement-list"></a>Lista de UIElement
 **Esquema de teclado de Visual Studio** Visual Studio recibe todos los comandos de tecla de método abreviado, aunque Excel tenga el foco. Por ejemplo, si presiona la tecla de función **F5** mientras Excel tiene el foco, Visual Studio inicia la depuración de la solución.

 **Esquema de teclado dinámico** Visual Studio recibe comandos de tecla de método abreviado solo cuando tiene el foco. Cuando Excel tiene el foco, Excel recibe todos los comandos de tecla de método abreviado. Por ejemplo, si presiona la tecla de función **F5** mientras Excel tiene el foco, Excel abre el cuadro de diálogo **ir a** . Si presiona **F5** mientras Visual Studio tiene el foco, Visual Studio inicia la depuración de la solución.

## <a name="see-also"></a>Vea también
- [Microsoft Office teclado de Word, Microsoft Office configuración del teclado, opciones (cuadro de diálogo)](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)
