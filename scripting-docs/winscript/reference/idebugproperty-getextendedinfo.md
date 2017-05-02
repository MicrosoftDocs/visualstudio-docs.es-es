---
title: "IDebugProperty::GetExtendedInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugProperty.GetExtendedInfo
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugProperty::GetExtendedInfo"
ms.assetid: a989ade5-16d5-4ee6-8d8a-8dcbfad24034
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugProperty::GetExtendedInfo
Gets extendidas información para la propiedad.  
  
## Sintaxis  
  
```  
HRESULT GetExtendedInfo (  
   ULONG  cInfos,  
   GUID*  rgguidExtendedInfo,  
   VARIANT* pExtendedInfo  
);  
```  
  
#### Parámetros  
 `cInfos`  
 \[in\] el recuento de información extendida se opone.  
  
 `rgguidExtendedInfo`  
 \[in\] matriz de s de `GUID`se pasa para poder recuperar varios elementos de información extendida al mismo tiempo.  
  
 `pExtendedInfo`  
 \[out\] devuelve una matriz de s de `VARIANT`que se puede utilizar para recuperar información extendida de la propiedad.  
  
## Valor devuelto  
 Devuelve `HRESULT`válido, normalmente `S_OK`.  
  
## Comentarios  
 Esta interfaz obtiene información extendida para este objeto.  API sólo existe con el fin de recuperar información que no se presta a recuperar por el uso de `IDebugProperty::GetPropertyInfo`\).  
  
## Vea también  
 [IDebugProperty \(Interfaz\)](../../winscript/reference/idebugproperty-interface.md)