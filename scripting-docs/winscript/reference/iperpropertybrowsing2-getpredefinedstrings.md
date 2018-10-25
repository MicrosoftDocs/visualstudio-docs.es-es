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
ms.openlocfilehash: a60225e69a04399a3ff0160291b84e9f3fda513c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49915972"
---
# <a name="iperpropertybrowsing2getpredefinedstrings"></a>IPerPropertyBrowsing2::GetPredefinedStrings
Permite al llamador rellenar un cuadro de lista con una matriz de punteros de cadena que representan los valores posibles para esta propiedad.  
  
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
 [in] Identificador de envío de la propiedad para el que el llamador está solicitando la lista de cadenas.  
  
 `pCaStrings`  
 [out] Puntero a una estructura de matriz asignada por el llamador contada que contiene el número de elementos y la dirección de una matriz asignada por el método de punteros de cadena. Si se produce un error en el método, no se asigna memoria y el contenido de la estructura es indefinido.  
  
 `pCaCookies`  
 [out] Puntero a la estructura de la matriz asignada por el llamador contada que contiene el número de elementos y la dirección de una matriz asignada por el método de DWORD. Si se produce un error en el método, no se asigna memoria y el contenido de la estructura es indefinido.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve un válidas `HRESULT`, normalmente `S_OK`.  
  
## <a name="see-also"></a>Vea también  
 [IPerPropertyBrowsing2 (Interfaz) 1](../../winscript/reference/iperpropertybrowsing2-interface-1.md)