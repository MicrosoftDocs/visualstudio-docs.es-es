---
title: Imprimir (Comando) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- debug.print
helpviewer_keywords:
- Debug.Print command
- Print method
- Print command
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 66175f8aa1d371386793b892c0ead5b4dd1885b0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="print-command"></a>Imprimir (Comando)
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
  
## <a name="see-also"></a>Vea también  
 [Evaluar instrucción (Comando)](../../ide/reference/evaluate-statement-command.md)   
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Ventana Comandos](../../ide/reference/command-window.md)   
 [Cuadro Buscar/Comando](../../ide/find-command-box.md)   
 [Alias de comandos de Visual Studio](../../ide/reference/visual-studio-command-aliases.md)