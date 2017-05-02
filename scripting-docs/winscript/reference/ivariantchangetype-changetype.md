---
title: "IVariantChangeType::ChangeType | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IVariantChangeType.ChangeType
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IVariantChangeType::ChangeType"
ms.assetid: 52374764-c42e-49af-a219-ee00c535a118
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IVariantChangeType::ChangeType
Toma un valor variable y crea un nuevo tipo Variant con un tipo especificado.  
  
## Sintaxis  
  
```  
HRESULT ChangeType(  
   VARIANT*  pvarDst,  
   VARIANT*  pvarSrc,  
   LCID  lcid,  
   VARTYPE  vtNew  
);  
```  
  
#### Parámetros  
 `pvarDst`  
 \[in, out\] variante de A para contener el valor representado por `pvarSrc`, pero con el tipo especificado por `vtNew`.  
  
 `pvarSrc`  
 \[in\] valor de variable de A cambiar en un nuevo tipo.  
  
 `lcid`  
 \[in\] contexto de la configuración regional de Va a utilizar al convertir los argumentos a o desde las cadenas.  
  
 `vtNew`  
 \[in\] especifica el tipo para que `pvarDst` sea.  
  
## Valor devuelto  
 El método devuelve un objeto `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Los argumentos de `pvarDst` y de `pvarSrc` pueden ser iguales, en cuyo caso se sobrescribe el valor original.  Este método pasa `pvarDst` a la función de `VariantClear` y, por consiguiente `pvarDst` se debe inicializar a un valor válido.  
  
## Vea también  
 [IVariantChangeType \(Interfaz\)](../../winscript/reference/ivariantchangetype-interface.md)