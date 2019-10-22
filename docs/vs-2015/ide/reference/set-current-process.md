---
title: Establecer el proceso actual | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c362d3f5dda5015e91ac88dd8f0abd60a185ba72
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665466"
---
# <a name="set-current-process"></a>Establecer el proceso actual
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Establece el proceso especificado como el proceso activo en el depurador.

## <a name="syntax"></a>Sintaxis

```
Debug.SetCurrentProcess index
```

## <a name="arguments"></a>Argumentos
 `index` Obligatorio. Índice del proceso.

## <a name="remarks"></a>Comentarios
 Puede asociar varios procesos mientras realiza la depuración, pero solo hay un proceso activo en el depurador en un momento determinado. Puede utilizar el comando `SetCurrentProcess` para establecer el proceso activo.

## <a name="example"></a>Ejemplo

```
>Debug.SetCurrentProcess 1
```

## <a name="see-also"></a>Otras referencias
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md) [ventana de comandos](../../ide/reference/command-window.md) de [Visual Studio alias de comandos](../../ide/reference/visual-studio-command-aliases.md)
