---
title: "Teclado de Microsoft Office Word, configuración de teclado de Microsoft Office, cuadro de diálogo Opciones | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Microsoft_Office_Tools.Microsoft_Office_Word.Keyboard
- VS.ToolsOptionsPages.Microsoft_Office_Keyboard_Settings.Microsoft_Office_Word_Keyboard
- VST.WordOptions.KeyboardMappingScheme
dev_langs:
- VB
- CSharp
helpviewer_keywords: keyboard shortcuts, Office development in Visual Studio
ms.assetid: d98edaab-846a-4baa-b190-702b1134754c
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 19e6e386a1d96fcadd788bb30f318de76e7f928f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box"></a>Teclado de Microsoft Office Word, Configuración de teclado de Microsoft Office, cuadro de diálogo Opciones
  Tanto Microsoft Office Word y Visual Studio admiten el uso de teclas de método abreviado. Puede ser la misma combinación de teclas de método abreviado para comandos diferentes en Word y en Visual Studio. Cuando Word está abierto en un proyecto de nivel de documento en Visual Studio, sólo una aplicación a la vez recibe los comandos de teclas de método abreviado. De forma predeterminada, Visual Studio recibe todos los comandos de teclas de método abreviado, pero puede hacer que Word recibirlos cuando el documento tiene el foco seleccionando **combinación de teclado dinámico**.  
  
 Si utiliza una tecla de método abreviado que no está asignada a un comando en la aplicación que actualmente se está controlando las teclas de método abreviado, la tecla de método abreviado se pasa a la otra aplicación.  
  
 La opción que seleccione permanecerá en vigor para los proyectos de Word hasta que la cambie. La selección no afecta a los proyectos de Microsoft Office Excel; debe realizar cualquier cambio en Excel mediante las opciones de teclado de Microsoft Office Excel.  
  
## <a name="uielement-list"></a>Lista de UIElement  
 **Combinación de teclado de Visual Studio**  
 Visual Studio recibe todos los comandos de teclas de método abreviado, incluso si el documento de Word tiene el foco. Por ejemplo, si presiona la tecla de función F5 mientras el documento tiene el foco, Visual Studio inicia la depuración de la solución.  
  
 **Combinación de teclado dinámico**  
 Visual Studio recibe los comandos de teclas de método abreviado sólo cuando tiene el foco. Cuando el documento de Word tiene el foco, Word recibe todos los comandos de teclas de método abreviado. Por ejemplo, si presiona la tecla de función F5 mientras el documento de Word tiene el foco, se abre Word la **buscar y reemplazar** cuadro de diálogo con el **ir a** ficha seleccionada. Si presiona F5 mientras Visual Studio tiene el foco, Visual Studio inicia la depuración de la solución.  
  
## <a name="see-also"></a>Vea también  
 [Teclado de Microsoft Office Excel, Configuración de teclado de Microsoft Office, cuadro de diálogo Opciones](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)  
  
  