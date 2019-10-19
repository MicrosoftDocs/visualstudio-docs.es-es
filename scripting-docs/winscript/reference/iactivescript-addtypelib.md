---
title: 'IActiveScript:: AddTypeLib | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.AddTypeLib
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_AddTypeLib
ms.assetid: 8e507ea8-c80a-471c-b482-ae753c6e8595
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 254a5133d42689020eaaae290a1016de4b848100
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575807"
---
# <a name="iactivescriptaddtypelib"></a>IActiveScript::AddTypeLib
Agrega una biblioteca de tipos al espacio de nombres para el script. Esto es similar a la Directiva `#include` en C/C++. Permite que un conjunto de elementos predefinidos como definiciones de clase, `typedefs` y constantes con nombre se agreguen al entorno en tiempo de ejecución disponible para el script.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT AddTypeLib(  
    REFGUID guidTypeLib,  // CLSID of type library  
    DWORD dwMaj,          // major version number  
    DWORD dwMin,          // minor version number  
    DWORD dwFlags         // option flags  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `guidTypeLib`  
 de CLSID de la biblioteca de tipos que se va a agregar.  
  
 `dwMaj`  
 de Número de versión principal.  
  
 `dwMin`  
 de Número de versión secundaria.  
  
 `dwFlags`  
 de Marcas de opciones. Puede ser el siguiente:  
  
|Valor|Significado|  
|-----------|-------------|  
|SCRIPTTYPELIB_ISCONTROL|La biblioteca de tipos describe un control ActiveX utilizado por el host.|  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve uno de los valores siguientes:  
  
|Valor devuelto|Significado|  
|------------------|-------------|  
|`S_OK`|Correcto.|  
|`E_INVALIDARG`|Un argumento no era válido.|  
|`E_UNEXPECTED`|No se esperaba la llamada (por ejemplo, el motor de scripting aún no se ha cargado o inicializado).|  
|`TYPE_E_CANTLOADLIBRARY`|No se pudo cargar la biblioteca de tipos especificada.|  
  
## <a name="see-also"></a>Vea también  
 [IActiveScript](../../winscript/reference/iactivescript.md)