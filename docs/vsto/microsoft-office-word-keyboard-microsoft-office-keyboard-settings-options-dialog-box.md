---
title: Teclado de Office Word, configuración, opciones (cuadro de diálogo)
description: Obtenga información acerca de cómo puede hacer que Microsoft Word reciba los comandos de tecla de método abreviado cuando el documento tiene el foco seleccionando esquema de teclado dinámico.
ms.custom: SEO-VS-2020
titleSuffix: ''
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
ms.openlocfilehash: bf4cfbaf23ad9c1e545af25614722cd52c493df7
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528437"
---
# <a name="microsoft-office-word-keyboard-settings-options-dialog-box"></a>Microsoft Office teclado de Word, configuración, opciones (cuadro de diálogo)
  Microsoft Office Word y Visual Studio controlan las teclas de método abreviado. La misma combinación de teclas de método abreviado puede tener distintos comandos en Word y en Visual Studio. Cuando Word está abierto en un proyecto de nivel de documento en Visual Studio, solo una aplicación a la vez recibe los comandos de tecla de método abreviado. De forma predeterminada, Visual Studio recibe todos los comandos de teclas de método abreviado, pero puede hacer que Word los reciba cuando el documento tenga el foco seleccionando **esquema de teclado dinámico**.

 Si usa una tecla de método abreviado que no está asignada a un comando en la aplicación que está controlando las teclas de método abreviado, la tecla de método abreviado se pasa a la otra aplicación.

 La opción que seleccione permanecerá en vigor para los proyectos de Word hasta que lo cambie. La selección no afecta a Microsoft Office proyectos de Excel; debe hacer cualquier cambio en Excel con las opciones del teclado de Excel Microsoft Office.

## <a name="uielement-list"></a>Lista de UIElement
 **Esquema de teclado de Visual Studio** Visual Studio recibe todos los comandos de tecla de método abreviado, aunque el documento de Word tenga el foco. Por ejemplo, si presiona la tecla de función **F5** mientras el documento tiene el foco, Visual Studio inicia la depuración de la solución.

 **Esquema de teclado dinámico** Visual Studio recibe comandos de tecla de método abreviado solo cuando tiene el foco. Cuando el documento de Word tiene el foco, Word recibe todos los comandos de tecla de método abreviado. Por ejemplo, si presiona la tecla de función **F5** mientras el documento de Word tiene el foco, Word abre el cuadro de diálogo **Buscar y reemplazar** con la ficha **ir a** seleccionada. Si presiona **F5** mientras Visual Studio tiene el foco, Visual Studio inicia la depuración de la solución.

## <a name="see-also"></a>Consulte también
- [Microsoft Office teclado de Excel, Microsoft Office configuración del teclado, opciones (cuadro de diálogo)](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)
