---
title: "IDebugProperty::EnumMembers | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugProperty.EnumMembers
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugProperty::EnumMembers"
ms.assetid: 8ce398a5-6452-4804-ae8f-5c54cd11c661
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugProperty::EnumMembers
Muestra los miembros de una propiedad.  
  
## Sintaxis  
  
```  
HRESULT EnumMembers (  
   DBGPROP_INFO_FLAGS dwFieldSpec,  
   UINT nRadix,  
   REFIID refiid,  
   IEnumDebugPropertyInfo** ppEnum  
);  
```  
  
#### Parámetros  
 `dwFieldSpec`  
 \[in\] especifica las constantes de `DBGPROP_INFO_FLAGS` que determinan qué campos en las estructuras enumeradas de la propiedad de depuración se deben completar.  
  
 `nRadix`  
 \[in\] base que se utilizará en la interpretación de cualquier información numérica.  
  
 `refiid`  
 \[in\] IID De se pasa para filtrar el enumerador.  El IID es una de las interfaces de `IDebugPropertyEnumType` que heredan de `IDebugPropertyEnumType_All`.  
  
 `ppEnum`  
 \[out\] devuelve la interfaz de `IEnumDebugPropertyInfo` que enumera las propiedades de miembro.  
  
## Valor devuelto  
 Devuelve `HRESULT`válido, normalmente `S_OK`.  
  
## Vea también  
 [IDebugProperty \(Interfaz\)](../../winscript/reference/idebugproperty-interface.md)   
 [DBGPROP\_INFO\_FLAGS](../../winscript/reference/dbgprop-info-flags.md)   
 [IDebugPropertyEnumType\_All \(Interfaz\)](../../winscript/reference/idebugpropertyenumtype-all-interface.md)   
 [IEnumDebugPropertyInfo \(Interfaz\)](../../winscript/reference/ienumdebugpropertyinfo-interface.md)