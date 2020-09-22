---
title: Referencia de API (depuración de Visual Studio) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], API reference
ms.assetid: e4e429da-3667-41f7-9158-a8207d13e91a
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f3e95200cf29c8561798c858635c3864d635fb40
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842594"
---
# <a name="api-reference-visual-studio-debugging"></a>Referencia de API (depuración de Visual Studio)
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La sección de referencia incluye información general conceptual de la API, una guía que muestra la sintaxis y el uso de todos los elementos de la API, así como una serie de ejemplos de código. Todas las referencias se enumeran alfabéticamente por categoría.  
  
 En la tabla siguiente se muestran los `HRESULT` valores comunes devueltos por los métodos.  
  
|Nombre|Descripción|Value|  
|----------|-----------------|-----------|  
|S_OK|Correcto.|0x00000000|  
|E_UNEXPECTED|Error inesperado.|0x8000FFFF|  
|E_NOTIMPL|Sin implementar.|0x80004001|  
|E_OUTOFMEMORY|Memoria insuficiente para completar la operación.|0x8007000E|  
|E_INVALIDARG|Uno o varios argumentos no son válidos.|0x80070057|  
|E_NOINTERFACE|No se admite esta interfaz.|0x80004002|  
|E_POINTER|Puntero no válido.|0x80004003|  
|E_HANDLE|Identificador no válido.|0x80070006|  
|E_ABORT|La operación se anuló.|0x80004004|  
|E_FAIL|Error inesperado.|0x80004005|  
|E_ACCESSDENIED|Error general de acceso denegado.|0x80070005|  
  
> [!NOTE]
> Cuando se [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] devuelve un método de depuración `S_OK` , se supone que todos los punteros de parámetro de salida son válidos; es decir, no se realiza ninguna validación en los punteros de parámetro out cuando `S_OK` se devuelve.  
  
> [!NOTE]
> Los parámetros no válidos o `NULL` [out] pueden hacer que el IDE se bloquee.  
  
## <a name="see-also"></a>Consulte también  
 [Interfaces](../../../extensibility/debugger/reference/interfaces-visual-studio-debugging.md)   
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [Aplicaciones auxiliares de SDK para depuración](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Extensibilidad del depurador de Visual Studio](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)
