---
title: Comando Ir a | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: edit.goto
helpviewer_keywords:
- Debug.Goto command
- Go To command
ms.assetid: 201e1dd2-6701-467d-8cc1-faec2ef20511
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9273cd908a8948b47b818e9c4333cb8bd70fe094
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="go-to-command"></a>Ir a (Comando)
Mueve el cursor a la línea especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Edit.GoTo [linenumber]  
```  
  
## <a name="arguments"></a>Argumentos  
 `linenumber`  
 Opcional. Entero que representa el número de la línea a la que se debe ir.  
  
## <a name="remarks"></a>Comentarios  
 La numeración de líneas empieza por el uno. Si el valor de `linenumber` es menor que uno, se muestra la primera línea. Si el valor de `linenumber` es mayor que el número de la última línea, se muestra la última línea.  
  
 Si no se especifica ningún valor para `linenumber`, se muestra el cuadro de diálogo **Ir a la línea**.  
  
 El alias de este comando es GoToLn.  
  
## <a name="example"></a>Ejemplo  
  
```  
>Edit.GoTo 125  
```  
  
## <a name="see-also"></a>Vea también  
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Ventana Comandos](../../ide/reference/command-window.md)   
 [Cuadro Buscar/Comando](../../ide/find-command-box.md)   
 [Alias de comandos de Visual Studio](../../ide/reference/visual-studio-command-aliases.md)