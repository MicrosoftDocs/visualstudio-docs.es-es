---
title: "SccIsMultiCheckoutEnabled (funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccIsMultiCheckoutEnabled"
helpviewer_keywords: 
  - "SccIsMultiCheckoutEnabled (función)"
ms.assetid: 6721639d-e475-4766-81b5-ee40a280fc70
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# SccIsMultiCheckoutEnabled (funci&#243;n)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esta función comprueba si el complemento de control de código fuente permite varias desprotecciones en un archivo.  
  
## Sintaxis  
  
```cpp#  
SCCRTN SccIsMultiCheckoutEnabled(  
   LPVOID pContext,  
   LPBOOL pbMultiCheckout  
);  
```  
  
#### Parámetros  
 pContext  
 \[in\] La estructura de contexto complemento de control de código fuente.  
  
 pbMultiCheckout  
 \[out\] Especifica si se habilitan varias desprotecciones para este proyecto \(distinto de cero significa que se admiten varias desprotecciones\).  
  
## Valor devuelto  
 La implementación de complemento del control de origen de esta función debe devolver uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC\_OK|La comprobación fue correcta.|  
|SCC\_E\_NONSPECIFICERROR<br /><br /> SCC\_E\_UNKNOWNERROR|Error no específico.|  
  
## Comentarios  
 El IDE realiza dos comprobaciones para determinar si los archivos pueden desproteger simultáneamente más de un usuario. En primer lugar, el sistema de control de código fuente debe admitir varias desprotecciones. El complemento de control de código fuente puede especificar esta funcionalidad durante la inicialización especificando el `SCC_CAP_MULTICHECKOUT`. Después, como una comprobación de segundo, el IDE llama a esta función para determinar si el proyecto actual admite varias desprotecciones. Si se admiten varias desprotecciones para el proyecto seleccionado, el complemento devuelve un éxito de código y establece `pbMultiCheckout` a cero \(`TRUE`\) o `FALSE`.  
  
## Vea también  
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)