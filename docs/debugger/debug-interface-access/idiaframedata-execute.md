---
title: "IDiaFrameData::execute | Microsoft Docs"
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
  - "IDiaFrameData::execute (método)"
ms.assetid: 7a6c7d03-1ff1-4059-bd54-5f407eeebc26
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaFrameData::execute
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Realiza la pila que desenredo y devuelve los resultados en una interfaz de cuadro de recorrido de pila.  
  
## Sintaxis  
  
```cpp#  
HRESULT execute (   
   IDiaStackWalkFrame* frame  
);  
```  
  
#### Parámetros  
 `frame`  
 \[in\]  Un objeto de [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) que contiene el estado del marco registra.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  la tabla siguiente muestra los valores devueltos posibles para este método.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|E\_DIA\_INPROLOG|No puede ejecutar un marco de pila mientras en código de prólogo.|  
|E\_DIA\_SYNTAX|Error de análisis encontrado en un programa de cuadro.|  
|E\_DIA\_FRAME\_ACCESS|No se puede obtener acceso a los registros o en memoria.|  
|E\_DIA\_VALUE|error en el cálculo de un valor \(por ejemplo, división por cero\).|  
  
## Comentarios  
 Se llama a este método durante la depuración desenrede la pila.  El objeto de [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) es implementado por la aplicación cliente para recibir las actualizaciones a los registros y proporcionar los métodos utilizados por el método de `execute` .  
  
## Vea también  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)