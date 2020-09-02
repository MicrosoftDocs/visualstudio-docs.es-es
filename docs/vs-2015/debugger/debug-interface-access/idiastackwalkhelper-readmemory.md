---
title: 'IDiaStackWalkHelper:: ReadMemory (| Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::readMemory method
ms.assetid: e1eb90aa-49b7-476c-9e70-7e8f08994cbe
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8bef01cd29bb2312bd682f2f1f1150ee78da293e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150065"
---
# <a name="idiastackwalkhelperreadmemory"></a>IDiaStackWalkHelper::readMemory
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Lee un bloque de datos de la imagen del archivo ejecutable en la memoria.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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
 de Un valor de la enumeración de [enumeración memorytypeenum (](../../debugger/debug-interface-access/memorytypeenum.md) que especifica el tipo de memoria que se va a leer.  
  
 va  
 de Dirección virtual de la imagen de la que se va a empezar a leer.  
  
 `cbData`  
 de Tamaño del búfer de datos en bytes.  
  
 `pcbData`  
 enuncia Devuelve el número de bytes leídos realmente. Si `pbData` es `NULL` , es el número total de bytes de datos disponibles.  
  
 `pbData`  
 [in, out] Búfer que se rellena con la lectura de memoria.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Consulte también  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [Enumeración MemoryTypeEnum](../../debugger/debug-interface-access/memorytypeenum.md)
