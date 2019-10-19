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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 18e585064bb50db7a0497c6b96e428a662e953ab
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72604827"
---
# <a name="watch-command"></a>Inspección (Comando)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Crea y abre una instancia especificada de una ventana **Inspección** . Puede usar una ventana **Inspección** para calcular los valores de variables, expresiones y registros, para editar estos valores y para guardar los resultados.

## <a name="syntax"></a>Sintaxis

```
Debug.Watch[index]
```

## <a name="arguments"></a>Argumentos
 `index` Obligatorio. El número de instancia de la ventana Inspección.

## <a name="remarks"></a>Comentarios
 `index` debe ser un entero. Los valores válidos son 1, 2, 3 o 4.

## <a name="example"></a>Ejemplo

```
>Debug.Watch1
```

## <a name="see-also"></a>Otras referencias
 [Ventanas automático y variables locales](../../debugger/autos-and-locals-windows.md) [Cómo: editar un valor en una ventana de variables](https://msdn.microsoft.com/library/36f464ab-c900-4c0b-9ab3-557b3d9cdab5) [Cómo: usar el cuadro de diálogo Inspección rápida](https://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867) ventana comandos de [Visual Studio](../../ide/reference/visual-studio-commands.md) [ventana de comandos](../../ide/reference/command-window.md) [Buscar/comando cuadros](../../ide/find-command-box.md) de comandos de [Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
