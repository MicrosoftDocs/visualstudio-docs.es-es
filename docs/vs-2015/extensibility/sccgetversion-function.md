---
title: SccGetVersion (función) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccGetVersion
helpviewer_keywords:
- SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 16a21ab75c8390f0bb5ff5f016f2bf5b8d04c3a3
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51779091"
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

