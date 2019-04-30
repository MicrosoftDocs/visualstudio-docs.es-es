---
title: IPerPropertyBrowsing2 (interfaz) 1 | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 156cf9a1e104b8a2d7ffe4e48bd39642ef1abbd0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62944904"
---
# <a name="iperpropertybrowsing2-interface-1"></a>IPerPropertyBrowsing2 (interfaz) 1
Tiene acceso a la información de las páginas de propiedades que ofrece un objeto.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|`GetDisplayString`|Devuelve una cadena de texto que describe la propiedad especificada.|  
|`MapPropertyToPage`|Devuelve el CLSID de la página de propiedades que permite la manipulación de la propiedad especificada.|  
|`GetPredefinedStrings`|Devuelve una matriz de cadenas (`LPOLESTR` punteros) lista de las descripciones de los valores permitidos que puede aceptar la propiedad especificada.|  
|`SetPredefinedValue`|Establece el valor de la propiedad en el valor predefinido identificado por el token `dwCookie.`|  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: dbgprop.h