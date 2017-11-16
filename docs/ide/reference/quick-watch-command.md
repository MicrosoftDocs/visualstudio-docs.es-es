---
title: "Inspección rápida (Comando) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: debug.quickwatch
helpviewer_keywords:
- Quick Watch command
- Debug.Quickwatch command
ms.assetid: 9670ac3a-8f2f-4874-974d-cb87d3b0cde1
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 081b12617e60d02a67a0d8eecbd70c35561f29a2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="quick-watch-command"></a>Inspección rápida (Comando)
Muestra el texto seleccionado o especificado en el campo Expresión de la ventana [Inspección rápida](../../debugger/watch-and-quickwatch-windows.md). Puede usar este cuadro de diálogo para calcular el valor actual de una variable o expresión reconocida por el depurador, o el contenido de un registro. Además, puede cambiar el valor de cualquier variable no constante o el contenido de cualquier registro.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Debug.QuickWatchq [text]  
```  
  
## <a name="arguments"></a>Argumentos  
 `text`  
 Opcional. El texto que se va a agregar al cuadro de diálogo **InspecciónRápida**.  
  
## <a name="remarks"></a>Comentarios  
 Si `text` se omite, el texto seleccionado actualmente o la palabra en el cursor se agrega a la ventana Inspección.  
  
## <a name="example"></a>Ejemplo  
  
```  
>Debug.QuickWatch  
```  
  
## <a name="see-also"></a>Vea también  
 [Set a Watch on Variables using the Watch and QuickWatch Windows in Visual Studio](../../debugger/watch-and-quickwatch-windows.md)  (Establecimiento de una ventana Inspección en variables que usan las ventanas Inspección e Inspección rápida en Visual Studio).  
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Ventana Comandos](../../ide/reference/command-window.md)   
 [Cuadro Buscar/Comando](../../ide/find-command-box.md)   
 [Alias de comandos de Visual Studio](../../ide/reference/visual-studio-command-aliases.md)