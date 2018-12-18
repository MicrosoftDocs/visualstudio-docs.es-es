---
title: IPerPropertyBrowsing2 (interfaz) 1 | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IPerPropertyBrowsing2
apilocation:
- scrobj.dll
helpviewer_keywords:
- IPerPropertyBrowsing2 interface
ms.assetid: 1e50b3f7-cc1c-495a-93c7-3ee03aea0b8a
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 75a0a7ef30bca2205789a63ea577808c11582791
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24728395"
---
# <a name="iperpropertybrowsing2-interface-1"></a>IPerPropertyBrowsing2 (interfaz) 1
Tiene acceso a la información de las páginas de propiedades que ofrece un objeto.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|`GetDisplayString`|Devuelve una cadena de texto que describe la propiedad especificada.|  
|`MapPropertyToPage`|Devuelve el CLSID de la página de propiedades que permite la manipulación de la propiedad especificada.|  
|`GetPredefinedStrings`|Devuelve una matriz unidimensional de cadenas (`LPOLESTR` punteros) enumerar las descripciones de los valores permitidos que puede aceptar la propiedad especificada.|  
|`SetPredefinedValue`|Establece el valor de la propiedad en el valor predefinido identificado por el token`dwCookie.`|  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: dbgprop.h