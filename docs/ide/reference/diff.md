---
title: -Diff
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 5377fedb-632a-4e86-a947-7c11c86451e7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6cbf0f8f9fa2e97908e2ae13e3961382a7250a91
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33704920"
---
# <a name="diff"></a>/Diferencias
Compara dos archivos. Las diferencias se muestran en una ventana especial de Visual Studio.

## <a name="syntax"></a>Sintaxis

```cmd
devenv /Diff SourceFile, TargetFile, [SourceDisplayName],[TargetDisplayName]
```

## <a name="arguments"></a>Argumentos
 `SourceFile`

 Obligatorio. Ruta de acceso completa y nombre del primer archivo que se va a comparar.

 `TargetFile`

 Obligatorio. Ruta de acceso completa y nombre del segundo archivo que se va a comparar.

 `SourceDisplayName`

 Opcional. Nombre para mostrar del primer archivo.

 `TargetDisplayName`

 Opcional. Nombre para mostrar del segundo archivo.