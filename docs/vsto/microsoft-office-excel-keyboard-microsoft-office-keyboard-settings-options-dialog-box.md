---
title: "Teclado de Microsoft Office Excel, Configuraci&#243;n de teclado de Microsoft Office, cuadro de di&#225;logo Opciones | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VST.ExcelOptions.KeyboardMappingScheme"
  - "VS.ToolsOptionsPages.Microsoft_Office_Keyboard_Settings.Microsoft_Office_Excel_Keyboard"
  - "VS.ToolsOptionsPages.Microsoft_Office_Tools.Microsoft_Office_Excel.Keyboard"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "métodos abreviados de teclado, desarrollo de Office en Visual Studio"
ms.assetid: 2a8b9e70-66fa-4461-8039-b6d8a2fbb963
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# Teclado de Microsoft Office Excel, Configuraci&#243;n de teclado de Microsoft Office, cuadro de di&#225;logo Opciones
  Tanto Microsoft Office Excel como Visual Studio admiten el uso de teclas de método abreviado.  La misma combinación de teclas de método abreviado puede corresponder a distintos comandos en Excel y en Visual Studio.  Cuando Excel se abre en un proyecto de nivel de documento en Visual Studio, solo una aplicación recibe a la vez los comandos de tecla de método abreviado.  De forma predeterminada, Visual Studio recibe todos los comandos de las teclas de método abreviado, pero puede hacer que los reciba Excel cuando el documento tenga el foco seleccionando la opción **Combinación de teclado dinámico**.  
  
 Si utiliza una tecla de método abreviado que no está asociada a ningún comando de la aplicación en la que se están utilizando las teclas de método abreviado, su efecto se pasa a la otra aplicación.  
  
 La opción seleccionada permanecerá en vigor para los proyectos de Excel hasta que la cambie.  La selección no afecta a los proyectos de Microsoft Office Word; debe realizar cualquier cambio para Word utilizando las opciones de teclado de Microsoft Office Word.  
  
## Lista de UIElement  
 **Combinación de teclado de Visual Studio**  
 Visual Studio recibe todos los comandos de teclas de método abreviado, incluso cuando Excel tiene el foco.  Por ejemplo, si presiona la tecla de función F5 mientras Excel tiene el foco, Visual Studio inicia la depuración de la solución.  
  
 **Combinación de teclado dinámico**  
 Visual Studio sólo recibe los comandos de teclas de método abreviado cuando está activo.  Cuando es Excel el que tiene foco, Excel recibe todos los comandos de las teclas de método abreviado.  Por ejemplo, si presiona la tecla de función F5 mientras Excel tiene el foco, Excel abre el cuadro de diálogo **Ir a**.  Si presiona F5 mientras Visual Studio tiene el foco, Visual Studio inicia la depuración de la solución.  
  
## Vea también  
 [Teclado de Microsoft Office Word, Configuración de teclado de Microsoft Office, cuadro de diálogo Opciones](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)  
  
  