---
title: SccGetVersion (función) | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccGetVersion
helpviewer_keywords:
- SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a4e548f1f2b82a97206cdf41174a8c1c7d61e885
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58988313"
---
# <a name="sccgetversion-function"></a>SccGetVersion (Función)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Esta función obtiene el número de versión de la API de complemento de Control de código fuente compatibles con el complemento de control de código fuente.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
LONG SccGetVersion(void);  
```  
  
#### <a name="parameters"></a>Parámetros  
 Ninguno.  
  
## <a name="return-value"></a>Valor devuelto  
 Un `LONG` tipo de datos que contiene el número de versión de la API de complemento de Control de origen compatibles:  
  
|WORD|Descripción|  
|----------|-----------------|  
|HIWORD|Versión principal|  
|LOWORD|Versión secundaria|  
  
## <a name="remarks"></a>Comentarios  
 Por ejemplo, si un complemento de control de origen es compatible con la versión 1.3 de la API de complemento de Control de origen, esta función debería devolver 0 x 0103.  
  
## <a name="see-also"></a>Vea también  
 [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
