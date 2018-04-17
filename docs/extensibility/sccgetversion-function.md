---
title: Función SccGetVersion | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccGetVersion
helpviewer_keywords:
- SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 70beb89f13d2f752f3adb0f25e2b370fa272171a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="sccgetversion-function"></a>SccGetVersion (función)
Esta función obtiene el número de versión de la API de complemento de Control de origen compatible con el complemento de control de código fuente.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
LONG SccGetVersion(void);  
```  
  
#### <a name="parameters"></a>Parámetros  
 Ninguno.  
  
## <a name="return-value"></a>Valor devuelto  
 A `LONG` tipo de datos que contiene el número de versión de la API de complemento de Control de origen compatible:  
  
|WORD|Descripción|  
|----------|-----------------|  
|HIWORD|Versión principal|  
|LOWORD|Versión secundaria|  
  
## <a name="remarks"></a>Comentarios  
 Por ejemplo, si un complemento de control de origen es compatible con la versión 1.3 de la API de complemento de Control de origen, esta función devolvería 0 x 0103.  
  
## <a name="see-also"></a>Vea también  
 [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)