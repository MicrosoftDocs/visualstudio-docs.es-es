---
title: 'Idiastackframe:: Get_rawlvarinstancevalue | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_rawLVarInstanceValue method
ms.assetid: ce526259-85a6-475b-9274-0b3a21d95db2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2c50b1db74674158d4c7304bbacb4105f387cd56
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
ms.locfileid: "31466856"
---
# <a name="idiastackframegetrawlvarinstancevalue"></a>IDiaStackFrame::get_rawLVarInstanceValue
Este método recupera el valor de la variable local especificada como bytes sin formato.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT get_rawLVarInstanceValue(  
   IDiaLVarInstance* pInstance,  
   DWORD             cbDataMax,  
   DWORD*            pcbData,  
   BYTE*             pbData  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pInstance`  
 [in] Un `IDiaLVarInstance` que representa una instancia de la variable local para obtener el valor para el objeto.  
  
 `cbDataMax`  
 [in] Número máximo de bytes en el búfer que señala `pbData`. Esto puede tener un máximo de 8 bytes (`sizeof(ULONGLONG)`).  
  
 `pcbData`  
 [out] Devuelve el número real de bytes almacenados en el búfer.  
  
 `pbData`  
 [out] Un búfer que se debe rellenar con datos. No puede ser `NULL`.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)