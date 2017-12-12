---
title: "Definición de tipo JsSerializedScriptUnloadCallback | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8d18c392-cca0-411e-9f2b-0d788b16161a
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6f485d31367f189231d354c653c8e58cc8656eb9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="jsserializedscriptunloadcallback-typedef"></a>JsSerializedScriptUnloadCallback (typedef)
El tiempo de ejecución llama a este typedef cuando finaliza con todos los recursos relacionados con la ejecución del script.     El llamador debe liberar el origen si está cargado, el código de bytes y el contexto en este momento.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
 typedef void (CALLBACK * JsSerializedScriptUnloadCallback)(  
  _In_ JsSourceContext sourceContext  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `sourceContext`  
 El contexto que se pasa a `JsParseSerializedScriptWithCallback` o `JsRunSerializedScriptWithCallback`.  
  
## <a name="remarks"></a>Comentarios  
  
> [!WARNING]
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jsrt.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia (tiempo de ejecución de JavaScript)](../chakra-hosting/reference-javascript-runtime.md)