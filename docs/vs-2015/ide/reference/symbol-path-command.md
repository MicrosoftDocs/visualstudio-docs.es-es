---
title: Comando Ruta de acceso de símbolos | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- debug.symbolpath
helpviewer_keywords:
- symbol path command
- Debug.SymbolPath command
- SymbolPath command
ms.assetid: b697ef2d-3f5d-40df-b113-7068a5bec0d4
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 343b45f4a8aef0fdeef5aef7653a5dbb1c7c5582
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49189168"
---
# <a name="symbol-path-command"></a>Ruta de acceso de símbolos (Comando)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Establece la lista de directorios para que el depurador busque símbolos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Debug.SymbolPath pathname1;pathname2;... pathnameN  
```  
  
## <a name="arguments"></a>Argumentos  
 `pathname`  
 Opcional. Lista de rutas de acceso delimitada por puntos y comas para que el depurador busque símbolos.  
  
## <a name="remarks"></a>Comentarios  
 Si no se especifica ningún `pathname`, el comando muestra las rutas de acceso de símbolos actuales.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo, se agregan dos rutas de acceso a la lista de directorios de símbolos.  
  
```  
Debug.SymbolPath C:\Symbol Path 1;C:\Symbol Path 2  
```  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo, se muestra una lista delimitada por puntos y comas de rutas de acceso de símbolos actuales.  
  
```  
Debug.SymbolPath  
```  
  
## <a name="see-also"></a>Vea también  
 [Ventana Comandos](../../ide/reference/command-window.md)   
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)



