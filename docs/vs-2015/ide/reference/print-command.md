---
title: Imprimir (Comando) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.print
helpviewer_keywords:
- Debug.Print command
- Print method
- Print command
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 65d78387c6d60d0b432db9aab175fbfe8dc2869b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68203565"
---
# <a name="print-command"></a>Imprimir (Comando)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Evalúa una expresión o muestra el texto especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Debug.Print text  
```  
  
## <a name="arguments"></a>Argumentos  
 `text`  
 Obligatorio. La expresión para evaluar o el texto para mostrar.  
  
## <a name="remarks"></a>Comentarios  
 Puede usar el signo de interrogación (?) como un alias para este comando. Por lo tanto, por ejemplo, el comando  
  
```  
>Debug.Print expA  
```  
  
 también se puede escribir  
  
```  
>? expA  
```  
  
 Ambas versiones de este comando devolverán el valor actual de la expresión `expA`.  
  
## <a name="example"></a>Ejemplo  
  
```  
>Debug.Print varA  
```  
  
## <a name="see-also"></a>Otras referencias  
 [Evaluar instrucción (Comando)](../../ide/reference/evaluate-statement-command.md)   
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Ventana Comandos](../../ide/reference/command-window.md)   
 [Cuadro Buscar/Comando](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
