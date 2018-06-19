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
ms.openlocfilehash: 9651197d24e96f58551bca5cfde5ec60b25bfa09
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
ms.locfileid: "31577319"
---
# <a name="resumetracking"></a>ResumeTracking
Reanuda el seguimiento en el contexto actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT WINAPI ResumeTracking();  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Un elemento **HRESULT** con el conjunto de bits **SUCCEEDED** si el seguimiento se ha reanudado. **E_FAIL** se devuelve si el seguimiento no puede reanudarse porque no está disponible el contexto.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** FileTracker.h  
  
## <a name="see-also"></a>Vea también  
 [SuspendTracking](../msbuild/suspendtracking.md)