---
title: IDiaStackWalkHelper::pdataForVA | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::pdataByVA method
ms.assetid: fafc38fe-74dc-4726-9a51-eebf3a673d7f
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 525a19a997d5902da5d69d5804281d472b5d6a26
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49906226"
---
# <a name="idiastackwalkhelperpdataforva"></a>IDiaStackWalkHelper::pdataForVA
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Devuelve el bloque de datos PDATA asociado con la dirección virtual.  
  
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
 [in] Especifica la dirección virtual de los datos que se va a obtener.  
  
 `cbData`  
 [in] El tamaño de datos en bytes para obtener.  
  
 `pcbData`  
 [out] Devuelve el tamaño real de los datos en bytes que se obtuvo.  
  
 `pbData`  
 [in, out] Un búfer que se rellena con los datos solicitados. No puede ser `NULL`.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`. Devuelve `S_FALSE` si no hay ningún PDATA para la dirección especificada. De lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 PDATA (la sección denominada ".pdata") de una operación de compilación contiene información sobre el control de excepciones de funciones.  
  
 El autor sabe es la cantidad de datos que se devuelve por lo que el llamador no tiene ninguna necesidad de solicitar la cantidad de datos está disponible. Por lo tanto, es aceptable para una implementación de este método para devolver un error si el `pbData` parámetro es `NULL`.  
  
## <a name="see-also"></a>Vea también  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)



