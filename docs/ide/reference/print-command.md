---
title: Imprimir (Comando) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: debug.print
helpviewer_keywords:
- Debug.Print command
- Print method
- Print command
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: bba20817c03b7ff542c3af11a440ad8e619f5567
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
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