---
title: IPerPropertyBrowsing2::GetPredefinedStrings | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IPerPropertyBrowsing2.GetPredefinedStrings
apilocation:
- scrobj.dll
helpviewer_keywords:
- IPerPropertyBrowsing2::GetPredefinedStrings
ms.assetid: d2fa30f7-a566-4dbd-8b47-ffdc00419771
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3bec9643a89d40a7b1e37d019d4211bd7167ee65
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088613"
---
# <a name="iperpropertybrowsing2getpredefinedstrings"></a>IPerPropertyBrowsing2::GetPredefinedStrings
Permite al llamador rellenar un cuadro de lista con una matriz de punteros de cadena que representan los valores posibles para esta propiedad.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetPredefinedStrings(  
   DISPID  dispid,  
   CALPOLESTR*  pCaStrings,  
   CADWORD*  pCaCookies  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dispid`  
 [in] Identificador de envío de la propiedad para el que el llamador está solicitando la lista de cadenas.  
  
 `pCaStrings`  
 [out] Puntero a una estructura de matriz asignada por el llamador contada que contiene el número de elementos y la dirección de una matriz asignada por el método de punteros de cadena. Si se produce un error en el método, no se asigna memoria y el contenido de la estructura es indefinido.  
  
 `pCaCookies`  
 [out] Puntero a la estructura de la matriz asignada por el llamador contada que contiene el número de elementos y la dirección de una matriz asignada por el método de DWORD. Si se produce un error en el método, no se asigna memoria y el contenido de la estructura es indefinido.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve un válidas `HRESULT`, normalmente `S_OK`.  
  
## <a name="see-also"></a>Vea también  
 [IPerPropertyBrowsing2 (Interfaz) 1](../../winscript/reference/iperpropertybrowsing2-interface-1.md)