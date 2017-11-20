---
title: "getVarDate (método, Date) (JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getVarDate
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Date object
- getVarDate method
- dates, VT_DATE format
ms.assetid: 561238de-5c91-45a3-b839-a16910d3a1cf
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d21394a5381653997a6b406537a6bde4f5266b97
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="getvardate-method-date-javascript"></a>getVarDate (Método, Date de JavaScript)
Devuelve un valor VT_DATE de un objeto `Date` .  
  
> [!WARNING]
>  Este método solo es válido en Internet Explorer.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
dateObj.getVarDate()   
```  
  
#### <a name="parameters"></a>Parámetros  
 La referencia a `dateObj` necesaria es un objeto `Date` .  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve un valor VT_DATE.  
  
## <a name="remarks"></a>Comentarios  
 El método `getVarDate` se usa cuando el código JavaScript interactúa con objetos COM, objetos ActiveX u otros objetos que aceptan y devuelven valores de fecha con el formato VT_DATE. Entre estos se incluyen los objetos en Visual Basic y Visual Basic Scripting Edition (VBScript). El formato real del valor devuelto depende de la configuración regional.  
  
## <a name="requirements"></a>Requisitos  
 Se admite en los siguientes modos de documento: Modo de interpretación, estándar de Internet Explorer 6, estándar de Internet Explorer 7, estándar de Internet Explorer 8, estándar de Internet Explorer 9 y estándar de Internet Explorer 10. No se admite en aplicaciones de [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] . Consulte [Información de versión](../../javascript/reference/javascript-version-information.md).  
  
 **Se aplica a**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [getDate (método, Date)](../../javascript/reference/getdate-method-date-javascript.md)   
 [Date.parse (Función)](../../javascript/reference/date-parse-function-javascript.md)