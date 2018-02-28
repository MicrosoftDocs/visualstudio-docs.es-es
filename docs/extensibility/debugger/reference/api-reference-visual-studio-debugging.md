---
title: "Referencia de API (depuración de Visual Studio) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], API reference
ms.assetid: e4e429da-3667-41f7-9158-a8207d13e91a
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 9f6e3110ca4988fcc12e547f3bcd82c1026f3aeb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="api-reference-visual-studio-debugging"></a>Referencia de API (depuración de Visual Studio)
La sección de referencia incluye información general y conceptual de la API, una guía que muestra la sintaxis y el uso para todos los elementos de la API y una gran variedad de ejemplos de código. Todas las referencias se muestran ordenados alfabéticamente por categoría.  
  
 La siguiente tabla muestra common `HRESULT` valores devueltos por métodos.  
  
|nombre|Descripción|Valor|  
|----------|-----------------|-----------|  
|S_OK|Correcto.|0x00000000|  
|E_UNEXPECTED|Error inesperado.|0x8000FFFF|  
|E_NOTIMPL|Sin implementar.|0 x 80004001|  
|E_OUTOFMEMORY|No hay suficiente memoria para completar la operación.|0x8007000E|  
|E_INVALIDARG|Uno o más argumentos no son válidos.|0 x 80070057|  
|E_NOINTERFACE|No se admite esta interfaz.|0 x 80004002|  
|E_POINTER|Puntero no válido.|0 x 80004003|  
|E_HANDLE|Identificador no válido.|0x80070006|  
|E_ABORT|Se anuló la operación.|0x80004004|  
|E_FAIL|Error inesperado.|0 x 80004005|  
|E_ACCESSDENIED|Error de denegación de acceso general.|0 x 80070005|  
  
> [!NOTE]
>  Cuando un [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] depurar el método devuelve `S_OK`, se asume que todo punteros de parámetro son válidos, es decir, que no se realiza ninguna validación en los punteros de parámetro cuando `S_OK` se devuelve.  
  
> [!NOTE]
>  No válido o `NULL` [parámetros out] puede hacer que el IDE se bloquee.  
  
## <a name="see-also"></a>Vea también  
 [Interfaces](../../../extensibility/debugger/reference/interfaces-visual-studio-debugging.md)   
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [Aplicaciones auxiliares SDK para la depuración](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Extensibilidad del depurador de Visual Studio](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)