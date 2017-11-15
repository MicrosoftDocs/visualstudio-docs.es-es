---
title: Establecer base (Comando) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: debug.setradix
helpviewer_keywords:
- Set Radix command
- Debug.SetRadix command
ms.assetid: 6ffd1554-7530-4da4-b5f5-e276a5034f3b
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 060221e5abe0ff9082a04f8b75561a7e4dec9f64
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="set-radix-command"></a>Establecer base (Comando)
Establece o devuelve la base numérica que se ha usado para mostrar valores enteros.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Debug.SetRadix [10 | 16 | hex | dec]  
```  
  
## <a name="arguments"></a>Argumentos  
 `10` o `16` o `hex` o `dec`  
 Opcional. Indica decimal (10 o dec) o hexadecimal (16 o hex). Si se omite un argumento, se devuelve el valor base actual.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo se establece el entorno para mostrar valores enteros en formato hexadecimal.  
  
```  
>Debug.SetRadix hex  
```  
  
## <a name="see-also"></a>Vea también  
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Ventana Comandos](../../ide/reference/command-window.md)   
 [Cuadro Buscar/Comando](../../ide/find-command-box.md)   
 [Alias de comandos de Visual Studio](../../ide/reference/visual-studio-command-aliases.md)