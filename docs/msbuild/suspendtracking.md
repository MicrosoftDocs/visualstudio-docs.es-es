---
title: SuspendTracking | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- SuspendTracking
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- SuspendTracking
ms.assetid: f5e06e5a-8083-444c-99c1-07ba834226b5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 70411d7279dd3f8023971546fd1d228298ce1634
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53911761"
---
# <a name="suspendtracking"></a>SuspendTracking
Suspende el seguimiento en el contexto actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp 
HRESULT WINAPI SuspendTracking(void);  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Un elemento **HRESULT** con el conjunto de bits **SUCCEEDED** si el seguimiento se ha suspendido.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado**: *FileTracker.h*  
  
## <a name="see-also"></a>Vea también  
 [ResumeTracking](../msbuild/resumetracking.md)