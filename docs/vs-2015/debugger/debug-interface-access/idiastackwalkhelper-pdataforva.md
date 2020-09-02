---
title: IDiaStackWalkHelper::pdataForVA | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::pdataByVA method
ms.assetid: fafc38fe-74dc-4726-9a51-eebf3a673d7f
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5af921caa989d7279bb9f52751c452d91045cf3e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150082"
---
# <a name="idiastackwalkhelperpdataforva"></a>IDiaStackWalkHelper::pdataForVA
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Devuelve el bloque de datos de PDATA asociado a la dirección virtual.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT pdataForVA(   
   ULONGLONG  va,  
   DWORD      cbData,  
   DWORD*     pcbData,  
   BYTE*      pbData  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `va`  
 de Especifica la dirección virtual de los datos que se van a obtener.  
  
 `cbData`  
 de Tamaño de los datos en bytes que se van a obtener.  
  
 `pcbData`  
 enuncia Devuelve el tamaño real de los datos en bytes obtenidos.  
  
 `pbData`  
 [in, out] Búfer que se rellena con los datos solicitados. El valor no puede ser `NULL`.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` si no hay ningún PDATA para la dirección especificada. De lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 PDATA (la sección denominada ". PDATA") de una operación de compilación contiene información sobre el control de excepciones para las funciones.  
  
 El autor de la llamada sabe cuántos datos se van a devolver, por lo que el autor de la llamada no tiene necesidad de solicitar la cantidad de datos disponibles. Por lo tanto, es aceptable que una implementación de este método devuelva un error si el `pbData` parámetro es `NULL` .  
  
## <a name="see-also"></a>Consulte también  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
