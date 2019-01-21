---
title: -Diff (devenv.exe)
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- Devenv, /Diff switch
- /Diff Devenv switch
- Diff Devenv switch
ms.assetid: 5377fedb-632a-4e86-a947-7c11c86451e7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cfe0fcdb039b4c7b234f3f43e6ce5741d96f5e9c
ms.sourcegitcommit: 01185dadd2fa1f9a040d2a366869f1a5e1d18e0f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/11/2019
ms.locfileid: "54227452"
---
# <a name="diff-devenvexe"></a>/Diff (devenv.exe)

Compara dos archivos. Las diferencias se muestran en una ventana especial de Visual Studio.

## <a name="syntax"></a>Sintaxis

```shell
devenv /Diff SourceFile TargetFile [SourceDisplayName [TargetDisplayName]]
```

## <a name="arguments"></a>Argumentos

- *SourceFile*

  Obligatorio. Ruta de acceso completa y nombre del primer archivo que se va a comparar.

- *TargetFile*

  Obligatorio. Ruta de acceso completa y nombre del segundo archivo que se va a comparar.

- *SourceDisplayName*

  Opcional. Nombre para mostrar del primer archivo.

- *TargetDisplayName*

  Opcional. Nombre para mostrar del segundo archivo.
    
## <a name="remarks"></a>Comentarios

Si ya hay abierta una instancia de IDE, la comparación de archivos se mostrará en una pestaña de IDE actual.

## <a name="example"></a>Ejemplo

En el primer ejemplo se comparan dos archivos sin cambiar sus nombres para mostrar. En el segundo, se comparan los archivos y se cambia el nombre para mostrar de ambos. En el tercero y el cuarto, se comparan los dos archivos, pero se aplica un alias únicamente al primer o al segundo archivo.

```shell
devenv /diff File1.txt File2.txt

devenv /diff File1.txt File2.txt FirstAlias "Second Alias"

devenv /diff File1.txt File2.txt "File One"

devenv /diff File1.txt File2.txt "" FileTwo
```

## <a name="see-also"></a>Vea también

- [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)
