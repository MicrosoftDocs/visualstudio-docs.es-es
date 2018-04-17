---
title: IDiaStackWalkHelper::readMemory | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::readMemory method
ms.assetid: e1eb90aa-49b7-476c-9e70-7e8f08994cbe
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: af93d4d49167a6167d971140c3b668c95a34f799
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idiastackwalkhelperreadmemory"></a>IDiaStackWalkHelper::readMemory
Lee un bloque de datos de imagen del archivo ejecutable en la memoria.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT readMemory(   
   enum MemoryTypeEnum type,  
   ULONGLONG           va,  
   DWORD               cbData,  
   DWORD*              pcbData,  
   BYTE*               pbData  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `type`  
 [in] Un valor de la [MemoryTypeEnum (enumeración)](../../debugger/debug-interface-access/memorytypeenum.md) enumeración que especifica el tipo de memoria para leer.  
  
 va  
 [in] Dirección virtual en la imagen desde el que se va a comenzar la lectura.  
  
 `cbData`  
 [in] El tamaño del búfer de datos en bytes.  
  
 `pcbData`  
 [out] Devuelve el número de bytes leídos realmente. Si `pbData` es `NULL`, este es el número total de bytes de datos disponibles.  
  
 `pbData`  
 [entrada, salida] Un búfer que se rellena con la memoria de lectura.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [MemoryTypeEnum (enumeración)](../../debugger/debug-interface-access/memorytypeenum.md)