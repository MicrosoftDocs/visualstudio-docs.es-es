---
title: IPerPropertyBrowsing2::GetPredefinedStrings | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IPerPropertyBrowsing2.GetPredefinedStrings
apilocation:
- scrobj.dll
helpviewer_keywords:
- IPerPropertyBrowsing2::GetPredefinedStrings
ms.assetid: d2fa30f7-a566-4dbd-8b47-ffdc00419771
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e07d52eca9434acc7e54f3b35b111cf12af0a871
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iperpropertybrowsing2getpredefinedstrings"></a>IPerPropertyBrowsing2::GetPredefinedStrings
Permite al llamador rellenar un cuadro de lista con una matriz unidimensional de punteros de cadena que representan los valores posibles para esta propiedad.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT GetPredefinedStrings(  
   DISPID  dispid,  
   CALPOLESTR*  pCaStrings,  
   CADWORD*  pCaCookies  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dispid`  
 [in] Identificador de envío de la propiedad para que el llamador solicita la lista de cadenas.  
  
 `pCaStrings`  
 [out] Puntero a una estructura de matriz asignada por el llamador, recuento que contiene el número de elementos y la dirección de una matriz de punteros de cadena asignada por el método. Si se produce un error en el método, no se asigna memoria y el contenido de la estructura es indefinido.  
  
 `pCaCookies`  
 [out] Puntero a la estructura de matriz asignada por el llamador, recuento que contiene el número de elementos y la dirección de una matriz asignada por el método de valores DWORD. Si se produce un error en el método, no se asigna memoria y el contenido de la estructura es indefinido.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve un válidas `HRESULT`, normalmente `S_OK`.  
  
## <a name="see-also"></a>Vea también  
 [IPerPropertyBrowsing2 (Interfaz) 1](../../winscript/reference/iperpropertybrowsing2-interface-1.md)