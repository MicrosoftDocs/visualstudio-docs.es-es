---
title: -Diff | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5377fedb-632a-4e86-a947-7c11c86451e7
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 14deeec64d4645135f19587997844bfdd0b18cd5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
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