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
ms.openlocfilehash: bded7159b72fc8c1ae8408611ce858105e6734da
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54344046"
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