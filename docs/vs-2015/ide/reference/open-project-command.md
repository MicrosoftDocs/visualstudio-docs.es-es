---
title: Comando Abrir proyecto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.openproject
helpviewer_keywords:
- op command
- File.OpenProject command
- Open Project command
ms.assetid: baa85f86-041b-49f4-9ced-0c397dc180e1
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 99596442f3aef9e4cb2d890438d29b96cdf4f083
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671918"
---
# <a name="open-project-command"></a>Abrir proyecto (Comando)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Abre un proyecto existente.

## <a name="syntax"></a>Sintaxis

```
File.OpenProject filename
```

## <a name="arguments"></a>Argumentos
 `filename` Obligatorio. Ruta de acceso completa y nombre de archivo del proyecto que se va a abrir.

 La sintaxis del argumento `filename` requiere que las rutas de acceso que contienen espacios se incluyan entre comillas.

## <a name="remarks"></a>Comentarios
 La finalización automática intenta localizar la ruta de acceso y el nombre de archivo correctos a medida que los va escribiendo.

 Este comando no está disponible durante la depuración.

## <a name="example"></a>Ejemplo
 En este ejemplo, se abre el proyecto Test1 de [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)].

```
>File.OpenProject "C:\My Projects\Test1\Test1.vbproj"
```

## <a name="see-also"></a>Otras referencias
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md) [ventana comandos](../../ide/reference/command-window.md) [Buscar/comando cuadro](../../ide/find-command-box.md) de comandos de [Visual Studio alias de comandos](../../ide/reference/visual-studio-command-aliases.md)
