---
title: ResumeTracking | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
apiname:
- ResumeTracking
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- ResumeTracking
ms.assetid: d637e019-7c50-4b0a-812e-bc822001e697
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2ec83d60046a74484035df9d7a7831d16b48d899
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/19/2018
ms.locfileid: "39151186"
---
# <a name="resumetracking"></a>ResumeTracking
Reanuda el seguimiento en el contexto actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT WINAPI ResumeTracking();  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Un elemento **HRESULT** con el conjunto de bits **SUCCEEDED** si el seguimiento se ha reanudado. **E_FAIL** se devuelve si el seguimiento no puede reanudarse porque no está disponible el contexto.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** *FileTracker.h*  
  
## <a name="see-also"></a>Vea también  
 [SuspendTracking](../msbuild/suspendtracking.md)