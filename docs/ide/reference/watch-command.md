---
title: Inspección (Comando) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- debug.watch
helpviewer_keywords:
- Watch command
- Debug.Watch command
ms.assetid: aa02e647-d9f5-4905-a651-52a8df595795
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a82816acfbb995b47dfb34337b20488ad3787f04
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="watch-command"></a>Inspección (Comando)
Crea y abre una instancia especificada de una ventana **Inspección** . Puede usar una ventana **Inspección** para calcular los valores de variables, expresiones y registros, para editar estos valores y para guardar los resultados.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Debug.Watch[index]  
```  
  
## <a name="arguments"></a>Argumentos  
 `index`  
 Obligatorio. El número de instancia de la ventana Inspección.  
  
## <a name="remarks"></a>Comentarios  
 `index` debe ser un entero. Los valores válidos son 1, 2, 3 o 4.  
  
## <a name="example"></a>Ejemplo  
  
```  
>Debug.Watch1  
```  
  
## <a name="see-also"></a>Vea también  
 [Ventanas de variables locales y automáticas](../../debugger/autos-and-locals-windows.md)   
 [Set a Watch on Variables using the Watch and QuickWatch Windows in Visual Studio](../../debugger/watch-and-quickwatch-windows.md)  (Establecimiento de una ventana Inspección en variables que usan las ventanas Inspección e Inspección rápida en Visual Studio).  
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Ventana Comandos](../../ide/reference/command-window.md)   
 [Cuadro Buscar/Comando](../../ide/find-command-box.md)   
 [Alias de comandos de Visual Studio](../../ide/reference/visual-studio-command-aliases.md)