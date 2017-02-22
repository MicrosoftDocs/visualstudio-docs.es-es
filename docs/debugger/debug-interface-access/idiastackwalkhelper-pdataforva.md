---
title: "IDiaStackWalkHelper::pdataForVA | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaStackWalkHelper2::pdataByVA (método)"
ms.assetid: fafc38fe-74dc-4726-9a51-eebf3a673d7f
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaStackWalkHelper::pdataForVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

devuelve el bloque de datos de PDATA asociado con la dirección virtual.  
  
## Sintaxis  
  
```cpp#  
HRESULT pdataForVA(   
   ULONGLONG  va,  
   DWORD      cbData,  
   DWORD*     pcbData,  
   BYTE*      pbData  
);  
```  
  
#### Parámetros  
 `va`  
 \[in\]  Especifica la dirección virtual de los datos para recopilar.  
  
 `cbData`  
 \[in\]  El tamaño de datos en bytes a recopilar.  
  
 `pcbData`  
 \[out\]  Devuelve el tamaño real de los datos en bytes recopilados.  
  
 `pbData`  
 \[in, out\]  Un búfer que se rellena con los datos solicitados.  No puede ser `NULL`.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`.  devuelve `S_FALSE` si no hay PDATA para la dirección especificada.  De lo contrario, devuelve un código de error.  
  
## Comentarios  
 El PDATA \(la sección denominada “.pdata”\) de una compilación contiene información sobre el control de excepciones para funciones.  
  
 El llamador sabe cuántos datos debe volver de modo que el llamador no tiene ninguna necesidad de ordenar cuántos datos está disponible.  Por consiguiente, es aceptable que una implementación de este método devuelve un error si el parámetro de `pbData` es `NULL`.  
  
## Vea también  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)