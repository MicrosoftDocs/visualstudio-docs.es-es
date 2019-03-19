---
title: IPerPropertyBrowsing2::GetPredefinedStrings | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 5a5f71ba91c65a8d99d831c777fc47fe9233fc18
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58157807"
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