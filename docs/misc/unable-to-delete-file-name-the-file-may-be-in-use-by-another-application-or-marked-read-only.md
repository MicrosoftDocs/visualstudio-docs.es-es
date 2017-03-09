---
title: "Unable to delete file &lt;name&gt;. The file may be in use by another application or marked read-only. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.VB_E_DELETEFILEFAILED"
  - "vs.message.0x800A00A2"
ms.assetid: 5c425dca-1d28-47a8-a11c-6a890be10baf
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Unable to delete file &lt;name&gt;. The file may be in use by another application or marked read-only.
Este error ocurre normalmente cuando el esquema de teclado seleccionado para eliminar está en uso o es de sólo lectura.  
  
### Para corregir este error  
  
1.  Si otra aplicación está usando el archivo especificado, ciérrela.  
  
     \-O bien\-  
  
     Si el archivo es de sólo lectura, quite el atributo de sólo lectura.  Puede modificar el atributo en el cuadro de diálogo Propiedades del archivo, disponible en el Explorador de archivos.  
  
## Vea también  
 [Identificar y personalizar métodos abreviados de teclado](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)