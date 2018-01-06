---
title: "Dónde buscar códigos de error de Win32 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.errors
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- error codes, Win32
- Win32, error codes
ms.assetid: 8fb4ff42-b8eb-4152-b49e-b802d194b05e
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f48f3fbff8f7f18fa745df7ac9571c69038651e6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="where-can-i-look-up-win32-error-codes"></a>Dónde buscar códigos de error de Win32
El archivo WINERROR.H, situado en el directorio INCLUDE de la instalación predeterminada del sistema, contiene las definiciones de código de error para las funciones de la API Win32.  
  
 Puede buscar un código de error escribiendo el código en el **inspección** ventana o el **Inspección rápida** cuadro de diálogo. Por ejemplo:  
  
```  
0x80000004,hr  
```  
  
## <a name="see-also"></a>Vea también  
 [Preguntas frecuentes sobre depuración de código nativo](../debugger/debugging-native-code-faqs.md)   
 [Depuración de código nativo](../debugger/debugging-native-code.md)