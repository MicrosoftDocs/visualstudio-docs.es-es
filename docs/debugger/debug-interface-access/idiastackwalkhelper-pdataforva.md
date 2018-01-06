---
title: IDiaStackWalkHelper::pdataForVA | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaStackWalkHelper2::pdataByVA method
ms.assetid: fafc38fe-74dc-4726-9a51-eebf3a673d7f
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 251b54ca712078e5252a4a55c9237545e14a7536
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idiastackwalkhelperpdataforva"></a>IDiaStackWalkHelper::pdataForVA
Devuelve el bloque de datos PDATA asociado con la dirección virtual.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
HRESULT pdataForVA(   
   ULONGLONG  va,  
   DWORD      cbData,  
   DWORD*     pcbData,  
   BYTE*      pbData  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `va`  
 [in] Especifica la dirección virtual de los datos que se va a obtener.  
  
 `cbData`  
 [in] El tamaño de los datos de bytes que se va a obtener.  
  
 `pcbData`  
 [out] Devuelve el tamaño real de los datos en bytes que se obtuvo.  
  
 `pbData`  
 [entrada, salida] Un búfer que se rellena con los datos solicitados. No puede ser `NULL`.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` si no hay ningún PDATA para la dirección especificada. De lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 PDATA (es decir, la sección denominada ".pdata") de una operación de compilación contiene información sobre el control de excepciones de funciones.  
  
 El llamador sabe cuántos datos se va a devolver para que el llamador no tiene necesidad de solicitar la cantidad de datos está disponible. Por lo tanto, es aceptable para una implementación de este método para devolver un error si la `pbData` parámetro es `NULL`.  
  
## <a name="see-also"></a>Vea también  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)