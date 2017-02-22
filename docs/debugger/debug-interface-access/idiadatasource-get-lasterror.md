---
title: "IDiaDataSource::get_lastError | Microsoft Docs"
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
  - "IDiaDataSource::get_lastError (método)"
ms.assetid: cf08850b-8b75-4e8c-90bd-bd0214756f99
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaDataSource::get_lastError
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

recupera el nombre de archivo para el error de carga pasado.  
  
## Sintaxis  
  
```cpp#  
HRESULT get_lastError (  
   BSTR* pRetVal  
);  
```  
  
#### Parámetros  
 pRetVal  
 \[out\]  Devuelve una cadena que contiene el nombre del archivo .pdb asociado al error de carga pasado.  
  
## Valor devuelto  
 Devuelve el último código de error provocado por una operación de carga.  devuelve `E_INVALIDARG` si el parámetro de `pRetVal` es `NULL`.  
  
## Ejemplo  
  
```cpp#  
BSTR    fileName;  
HRESULT errorCode = pSource->get_lastError( &fileName );  
```  
  
## Vea también  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)