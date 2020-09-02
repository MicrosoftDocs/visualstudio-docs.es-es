---
title: Comando Agregar proyecto existente | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.addexistingproject
helpviewer_keywords:
- Add Existing Project command
- File.AddExistingProject
ms.assetid: 71cf3e31-c76b-405b-ad6a-1b1bc654bd40
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 73d8e54938659920227b3614046b8a8f933023ff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670214"
---
# <a name="add-existing-project-command"></a>Agregar proyecto existente (Comando)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Agrega un proyecto existente a la solución actual.

## <a name="syntax"></a>Sintaxis

```
File.AddExistingProject filename
```

## <a name="arguments"></a>Argumentos
 `filename` Opcional. El nombre del proyecto y la ruta de acceso completa, con extensión, del proyecto que se agregará a la solución.

 Si el argumento `filename` incluye espacios, debe incluirse entre comillas.

 Si no se especifica ningún nombre de archivo, el comando abrirá el cuadro de diálogo de archivo para que el usuario pueda elegir un proyecto.

## <a name="remarks"></a>Observaciones
 La finalización automática intenta localizar la ruta de acceso y el nombre de archivo correctos a medida que los va escribiendo.

## <a name="example"></a>Ejemplo
 En este ejemplo, se agrega el proyecto TestProject1 de [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] a la solución actual.

```
>File.AddExistingProject "c:\visual studio projects\TestProject1.vbproj"
```

## <a name="see-also"></a>Consulte también
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md) [ventana comandos](../../ide/reference/command-window.md) [Buscar/comando cuadro](../../ide/find-command-box.md) de comandos de [Visual Studio alias de comandos](../../ide/reference/visual-studio-command-aliases.md)
