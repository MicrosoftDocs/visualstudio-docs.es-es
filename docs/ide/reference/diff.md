---
title: -Diff | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
ms.assetid: 5377fedb-632a-4e86-a947-7c11c86451e7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 016de0a06615caab723f83900e8bd4103cb142b1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="diff"></a>/Diferencias
Compara dos archivos. Las diferencias se muestran en una ventana especial de Visual Studio.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
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