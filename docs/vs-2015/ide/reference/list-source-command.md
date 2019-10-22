---
title: Mostrar código fuente (Comando) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- Debug.ListSource
helpviewer_keywords:
- Debug.ListSource command
- list source command
- ListSource command
ms.assetid: e45f08d2-f4a3-49c3-9452-aa60508e2f74
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3f13689b6e3ac4db2d58c1def3a5d0dd05c219f2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672317"
---
# <a name="list-source-command"></a>Mostrar código fuente (Comando)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Muestra las líneas de código fuente especificadas.

## <a name="syntax"></a>Sintaxis

```
Debug.ListSource [/Count:number] [/Current] [/File:filename]
[/Line:number] [/ShowLineNumbers:yes|no]
```

## <a name="switches"></a>Modificadores
 /Count: `number` opcional. Especifica el número de líneas que se van a mostrar.

 /Current opcional. Muestra la línea actual.

 /File: `filename` opcional. Ruta de acceso del archivo que se va a mostrar. Si no se especifica ningún nombre de archivo, el comando muestra el código fuente para la línea de la instrucción actual.

 /Line: `number` opcional. Muestra un número de línea concreto.

 /ShowLineNumbers: `yes|no` opcional. Especifica si se mostrarán o no los números de línea.

## <a name="remarks"></a>Comentarios

## <a name="example"></a>Ejemplo
 En este ejemplo se muestra el código fuente desde la línea 4 del archivo Form1.vb, con los números de línea visibles.

```
Debug.ListSource /File:"C:\Visual Studio Projects\Form1.vb" /Line:4 /ShowLineNumbers:yes
```

## <a name="see-also"></a>Otras referencias
 [Ventana](../../ide/reference/command-window.md) comandos de [comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)
