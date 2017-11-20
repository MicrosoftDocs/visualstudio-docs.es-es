---
title: IActiveScript::AddTypeLib | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScript.AddTypeLib
apilocation: scrobj.dll
helpviewer_keywords: IActiveScript_AddTypeLib
ms.assetid: 8e507ea8-c80a-471c-b482-ae753c6e8595
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a2be7cf033b4b5dd4d99b19a3b71ed53e32af855
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptaddtypelib"></a>IActiveScript::AddTypeLib
Agrega una biblioteca de tipos para el espacio de nombres para la secuencia de comandos. Esto es similar a la `#include` la directiva de C o C++. Permite que un conjunto de elementos predefinidos, como las definiciones de clase, `typedefs`y constantes con nombre que se agregan al entorno de tiempo de ejecución disponible para la secuencia de comandos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT AddTypeLib(  
    REFGUID guidTypeLib,  // CLSID of type library  
    DWORD dwMaj,          // major version number  
    DWORD dwMin,          // minor version number  
    DWORD dwFlags         // option flags  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `guidTypeLib`  
 [in] CLSID de la biblioteca de tipos para agregar.  
  
 `dwMaj`  
 [in] Número de versión principal.  
  
 `dwMin`  
 [in] Número de versión secundaria.  
  
 `dwFlags`  
 [in] Marcas de opción. Puede ser el siguiente:  
  
|Valor|Significado|  
|-----------|-------------|  
|SCRIPTTYPELIB_ISCONTROL|La biblioteca de tipos describe un control ActiveX utilizado por el host.|  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve uno de los siguientes valores:  
  
|Valor devuelto|Significado|  
|------------------|-------------|  
|`S_OK`|Correcto.|  
|`E_INVALIDARG`|Un argumento no era válido.|  
|`E_UNEXPECTED`|No se esperaba la llamada (por ejemplo, el motor de scripting se aún no ha cargado o inicializar).|  
|`TYPE_E_CANTLOADLIBRARY`|No se pudo cargar la biblioteca de tipos especificado.|  
  
## <a name="see-also"></a>Vea también  
 [IActiveScript](../../winscript/reference/iactivescript.md)