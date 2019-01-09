---
title: IDebugSyncOperation::InProgressAbort | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugSyncOperation.InProgressAbort
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugSyncOperation::InProgressAbort
ms.assetid: bfd0889c-b627-4843-b1c6-b6b918f42d61
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cab8bae7f131d24c1a2c7272dc8d1178e12bf0e6
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54095529"
---
# <a name="idebugsyncoperationinprogressabort"></a>IDebugSyncOperation::InProgressAbort
Cancela una operación en curso en otro subproceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT InProgressAbort();  
```  
  
#### <a name="parameters"></a>Parámetros  
 Este método no toma ningún parámetro.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`E_NOTIMPL`|No se puede cancelar la operación.|  
|`E_ABORT`|No se pudo completar la operación.|  
  
## <a name="remarks"></a>Comentarios  
 El Administrador de procesos de depuración llama a este método desde el subproceso del depurador para cancelar una operación que está en curso en otro subproceso.  
  
 Si el `InProgressAbort` método no puede completar la operación, devuelve `E_ABORT` tan pronto como sea posible. Este método puede devolver `E_NOTIMPL` si no se puede cancelar la operación.  
  
## <a name="see-also"></a>Vea también  
 [IDebugSyncOperation (Interfaz)](../../winscript/reference/idebugsyncoperation-interface.md)