---
title: Establecer base (Comando) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.setradix
helpviewer_keywords:
- Set Radix command
- Debug.SetRadix command
ms.assetid: 6ffd1554-7530-4da4-b5f5-e276a5034f3b
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c315ccb0bc7404ddbaa303430644b404a570e016
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54798095"
---
# <a name="set-radix-command"></a>Establecer base (Comando)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
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
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
