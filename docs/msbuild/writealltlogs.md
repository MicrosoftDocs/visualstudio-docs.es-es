---
title: WriteAllTLogs | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
apiname: WriteAllTLogs
apilocation: filetracker.dll
apitype: COM
helpviewer_keywords: WriteAllTLogs
ms.assetid: 1fa3e10b-263c-4960-a9ad-485c02a7a872
caps.latest.revision: "5"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8abc76ef0c9d3e04f0aae676af0bfa20183b3a8d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="writealltlogs"></a>WriteAllTLogs
Escribe registros de seguimiento para todos los subprocesos y contextos.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT WINAPI WriteAllTLogs(LPCTSTR intermediateDirectory, LPCTSTR tlogRootName);  
```  
  
#### <a name="parameters"></a>Parámetros  
 [in] `intermediateDirectory`  
 El directorio en el que almacenar el registro de seguimiento.  
  
 [in] `tlogRootName`  
 El nombre raíz del nombre del archivo de registro.  
  
## <a name="return-value"></a>Valor devuelto  
 Un elemento **HRESULT** con el conjunto de bits **SUCCEEDED** si el contexto de seguimiento se ha creado.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** FileTracker.h  
  
## <a name="see-also"></a>Vea también  
 [WriteContextTLogs](../msbuild/writecontexttlogs.md)