---
title: "Referencia de la API (depuraci&#243;n de Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "depurar [SDK de depuración], referencia de API"
ms.assetid: e4e429da-3667-41f7-9158-a8207d13e91a
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# Referencia de la API (depuraci&#243;n de Visual Studio)
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

La sección de referencia incluye una introducción general de la API, una guía que muestra la sintaxis y el uso para todos los elementos de la API, y de una serie de ejemplos de código.  todas las referencias son enumeradas alfabéticamente por categoría.  
  
 La tabla siguiente se muestran los valores de `HRESULT` de común devueltos por métodos.  
  
|Name|Descripción|Valor|  
|----------|-----------------|-----------|  
|S\_OK|Correcto.|0x00000000|  
|E\_UNEXPECTED|error inesperado.|0x8000FFFF|  
|E\_NOTIMPL|Sin implementar.|0x80004001|  
|E\_OUTOFMEMORY|Memoria insuficiente para completar la operación.|0x8007000E|  
|E\_INVALIDARG|Uno o varios argumentos no son válidos.|0x80070057|  
|E\_NOINTERFACE|Ninguna como interfaz compatible.|0x80004002|  
|E\_POINTER|Puntero no válido.|0x80004003|  
|E\_HANDLE|Identificador no válido.|0x80070006|  
|E\_ABORT|operación anulada.|0x80004004|  
|E\_FAIL|error inesperado.|0x80004005|  
|E\_ACCESSDENIED|error general de acceso denegado.|0x80070005|  
  
> [!NOTE]
>  Cuando [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] de depuración método devuelve `S_OK`, se supone que todo out punteros de parámetro es válido, es decir, no se realiza ninguna validación de out punteros de parámetro cuando se devuelve `S_OK` .  
  
> [!NOTE]
>  Los parámetros no válidos o \[out\] de `NULL` pueden producir el IDE al bloqueo.  
  
## Vea también  
 [Interfaces](../../../extensibility/debugger/reference/interfaces-visual-studio-debugging.md)   
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [Aplicaciones auxiliares SDK para la depuración](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Extensibilidad del depurador de Visual Studio](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)