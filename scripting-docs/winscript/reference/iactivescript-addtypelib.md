---
title: "IActiveScript::AddTypeLib | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.AddTypeLib
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_AddTypeLib"
ms.assetid: 8e507ea8-c80a-471c-b482-ae753c6e8595
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScript::AddTypeLib
Agrega una biblioteca de tipos al espacio de nombres para el script.  Esto es similar a la directiva de `#include` en C\/C\+\+.  Permite a un conjunto de elementos predefinidos como las definiciones de clase, `typedefs`, y constantes con nombre que se van a agregar al entorno en tiempo de ejecución disponibles para el script.  
  
## Sintaxis  
  
```  
HRESULT AddTypeLib(  
    REFGUID guidTypeLib,  // CLSID of type library  
    DWORD dwMaj,          // major version number  
    DWORD dwMin,          // minor version number  
    DWORD dwFlags         // option flags  
);  
```  
  
#### Parámetros  
 `guidTypeLib`  
 \[in\] el CLSID de la biblioteca de tipos a agregar.  
  
 `dwMaj`  
 \[in\] número de versión principales.  
  
 `dwMin`  
 \[in\] número de versión de Minor.  
  
 `dwFlags`  
 \[in\] marcas de opción.  Puede ser el siguiente:  
  
|Valor|Significado|  
|-----------|-----------------|  
|SCRIPTTYPELIB\_ISCONTROL|La biblioteca de tipos describe un control ActiveX utilizado por el host.|  
  
## Valor devuelto  
 Devuelve uno de los siguientes valores:  
  
|Valor devuelto|Significado|  
|--------------------|-----------------|  
|`S_OK`|Correcto.|  
|`E_INVALIDARG`|Un argumento no era válido.|  
|`E_UNEXPECTED`|La llamada no se esperaba \(por ejemplo, el motor de script aún no se han cargado no se ha inicializado\).|  
|`TYPE_E_CANTLOADLIBRARY`|La biblioteca de tipos especificada no pudo cargarse.|  
  
## Vea también  
 [IActiveScript](../../winscript/reference/iactivescript.md)