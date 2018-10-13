---
title: Dónde buscar códigos de error de Win32 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vc.errors
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- error codes, Win32
- Win32, error codes
ms.assetid: 8fb4ff42-b8eb-4152-b49e-b802d194b05e
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ce5cc450c05ee759d4d65e22394c6ef814b0a872
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49206003"
---
# <a name="where-can-i-look-up-win32-error-codes"></a>Dónde buscar códigos de error de Win32
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El archivo WINERROR.H, situado en el directorio INCLUDE de la instalación predeterminada del sistema, contiene las definiciones de código de error para las funciones de la API Win32.  
  
 Puede buscar un código de error escribiendo el código en el **inspección** ventana o el **Inspección rápida** cuadro de diálogo. Por ejemplo:  
  
```  
0x80000004,hr  
```  
  
## <a name="see-also"></a>Vea también  
 [Preguntas frecuentes sobre depuración de código nativo](../debugger/debugging-native-code-faqs.md)   
 [Depuración de código nativo](../debugger/debugging-native-code.md)



