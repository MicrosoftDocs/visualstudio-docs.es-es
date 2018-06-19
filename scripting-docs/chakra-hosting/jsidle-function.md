---
title: Función JsIdle | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- jsrt/JsIdle
helpviewer_keywords:
- JsIdle function
ms.assetid: 372d1c62-8e19-4886-aa33-364cabc09bba
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ddffd4f37c0e10985a2dbca26558d8a94b21b2f7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568815"
---
# <a name="jsidle-function"></a>JsIdle (Función)
Indica al runtime que realice el procesamiento en inactividad que sea necesario.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
STDAPI_(JsErrorCode) JsIdle(  
   _Out_opt_ unsigned int *nextIdleTick  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `nextIdleTick`  
 El siguiente paso del sistema en el que habrá más tareas inactivas que realizar. Puede ser NULL. Devuelve el número de pasos máximo si no hay ninguna tarea inactiva próxima que realizar.  
  
## <a name="return-value"></a>Valor devuelto  
 El código `JsNoError` si la operación se realizó correctamente; en caso contrario, un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Si se ha habilitado el procesamiento en inactividad para el runtime actual, la llamada a `JsIdle` informará a este de que el host está inactivo y que el runtime puede realizar tareas de limpieza de memoria.  
  
 `JsIdle` también puede devolver el número de pasos del sistema hasta que el runtime tenga más tareas inactivas que realizar. Si se llama a `JsIdle` antes de que haya transcurrido este número de pasos, no se realizará ningún trabajo.  
  
 Requiere un contexto de script activo.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jsrt.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia (tiempo de ejecución de JavaScript)](../chakra-hosting/reference-javascript-runtime.md)