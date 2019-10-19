---
title: 'Iperpropertybrowsing2 (:: GetPredefinedStrings | Microsoft Docs'
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
ms.openlocfilehash: 55ade724dd9ee5d59feb9d04c5b525ca839a9cec
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576775"
---
# <a name="iperpropertybrowsing2getpredefinedstrings"></a>IPerPropertyBrowsing2::GetPredefinedStrings
Permite al llamador rellenar un cuadro de lista con una matriz contada de punteros de cadena que representan valores posibles para esta propiedad.  
  
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
 de Identificador de envío de la propiedad para la que el autor de la llamada solicita la lista de cadenas.  
  
 `pCaStrings`  
 enuncia Puntero a una estructura de matriz contada asignada por el llamador que contiene el recuento de elementos y la dirección de una matriz de punteros de cadena asignada a un método. Si se produce un error en el método, no se asigna ninguna memoria y el contenido de la estructura es indefinido.  
  
 `pCaCookies`  
 enuncia Puntero a la estructura de la matriz contada asignada por el llamador que contiene el recuento de elementos y la dirección de una matriz de DWORD asignada a un método. Si se produce un error en el método, no se asigna ninguna memoria y el contenido de la estructura es indefinido.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve un `HRESULT` válido, normalmente `S_OK`.  
  
## <a name="see-also"></a>Vea también  
 [IPerPropertyBrowsing2 (Interfaz) 1](../../winscript/reference/iperpropertybrowsing2-interface-1.md)