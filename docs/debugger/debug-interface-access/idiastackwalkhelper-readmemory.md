---
title: IDiaStackWalkHelper::readMemory | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: 14a8e435dddaf0d6fb3908a1ccb6233f08ccd28b
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
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