---
title: Inspección (Comando) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.watch
helpviewer_keywords:
- Watch command
- Debug.Watch command
ms.assetid: aa02e647-d9f5-4905-a651-52a8df595795
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b1a04dce73dbf2551b51f2395b3512e62daf3766
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54788195"
---
# <a name="watch-command"></a>Inspección (Comando)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
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
 [Cómo: Modificar un valor en una ventana de variables](http://msdn.microsoft.com/library/36f464ab-c900-4c0b-9ab3-557b3d9cdab5)   
 [Cómo: Utilice el cuadro de diálogo Inspección rápida](http://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867)   
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Ventana Comandos](../../ide/reference/command-window.md)   
 [Cuadro Buscar/Comando](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
