---
title: Comando Ruta de acceso de símbolos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- debug.symbolpath
helpviewer_keywords:
- symbol path command
- Debug.SymbolPath command
- SymbolPath command
ms.assetid: b697ef2d-3f5d-40df-b113-7068a5bec0d4
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b1b35c5d55eed31111746f2e2dbf9befb4fb7591
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="symbol-path-command"></a>Ruta de acceso de símbolos (Comando)
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