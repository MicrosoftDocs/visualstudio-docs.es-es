---
title: "Teclado de Microsoft Office Word, Configuraci&#243;n de teclado de Microsoft Office, cuadro de di&#225;logo Opciones | Microsoft Docs"
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
  - "VS.ToolsOptionsPages.Microsoft_Office_Tools.Microsoft_Office_Word.Keyboard"
  - "VS.ToolsOptionsPages.Microsoft_Office_Keyboard_Settings.Microsoft_Office_Word_Keyboard"
  - "VST.WordOptions.KeyboardMappingScheme"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "métodos abreviados de teclado, desarrollo de Office en Visual Studio"
ms.assetid: d98edaab-846a-4baa-b190-702b1134754c
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# Teclado de Microsoft Office Word, Configuraci&#243;n de teclado de Microsoft Office, cuadro de di&#225;logo Opciones
  Tanto Microsoft Office Word como Visual Studio admiten el uso de teclas de método abreviado.  La misma combinación de teclas de método abreviado puede representar comandos diferentes en Word y en Visual Studio.  Cuando Word se abre en un proyecto de nivel de documento en Visual Studio, solo una aplicación recibe a la vez los comandos de tecla de método abreviado.  De forma predeterminada, Visual Studio recibe todos los comandos de las teclas de método abreviado, pero puede hacer que los reciba Word cuando el documento tenga el foco seleccionando la opción **Combinación de teclado dinámico**.  
  
 Si utiliza una tecla de método abreviado que no está asociada a ningún comando de la aplicación en la que se están utilizando las teclas de método abreviado, su efecto se pasa a la otra aplicación.  
  
 La opción que se selecciona permanecerá en vigor para los proyectos de Word hasta que se cambie.  La selección no afecta a los proyectos de Microsoft Office Excel; los cambios en Excel deben realizarse con las opciones de teclado de Microsoft Office Excel.  
  
## Lista de UIElement  
 **Combinación de teclado de Visual Studio**  
 Visual Studio recibe todos los comandos de teclas de método abreviado, incluso cuando el documento de Word tiene el foco.  Por ejemplo, si se presiona la tecla de función F5 mientras el documento está activo, Visual Studio inicia la depuración de la solución.  
  
 **Combinación de teclado dinámico**  
 Visual Studio sólo recibe los comandos de teclas de método abreviado cuando está activo.  Cuando es el documento de Word el que tiene el foco, Word recibe todos los comandos de las teclas de método abreviado.  Por ejemplo, si se presiona la tecla de función F5 mientras el documento de Word está activo, Word abre el cuadro de diálogo **Buscar y reemplazar** con la ficha **Ir a** seleccionada.  Si presiona F5 mientras Visual Studio tiene el foco, Visual Studio inicia la depuración de la solución.  
  
## Vea también  
 [Teclado de Microsoft Office Excel, Configuración de teclado de Microsoft Office, cuadro de diálogo Opciones](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)  
  
  