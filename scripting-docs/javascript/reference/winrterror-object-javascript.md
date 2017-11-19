---
title: WinRTError (objeto) (JavaScript) | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- WinRTError object [JavaScript]
- JavaScript, WinRTError object
ms.assetid: d75ab8e5-e729-4d86-90fd-ea228c30dd66
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 11b339b4fc3c4bd4f34416ffd98b8f9c3f288f98
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="winrterror-object-javascript"></a>WinRTError (Objeto de JavaScript)
Si una llamada a Windows Runtime devuelve un valor HRESULT que indica un error, JavaScript lo convierte en un error especial de Windows Runtime. Este objeto solo está disponible en aplicaciones de la [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] (si Windows en tiempo de ejecución está disponible) como parte del espacio de nombres global de JavaScript.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
errorObj = new WinRTError();  
  
```  
  
## <a name="remarks"></a>Comentarios  
 El tipo de error WinRTError se usa únicamente para errores que se originan en las API de Windows Runtime.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra la forma en que se produce y se detecta un WinRTError.  
  
```JavaScript  
try {  
            Windows.Storage.ApplicationData.localFolder.createFileAsync("sample.txt");  
        } catch (err) {  
            var n = err;  
        }  
  
```  
  
## <a name="methods"></a>Métodos  
 El objeto WinRTError no tiene métodos.  
  
## <a name="properties"></a>Propiedades  
 El objeto WinRTError tiene las mismas propiedades como el [objeto Error](../../javascript/reference/error-object-javascript.md) objeto.  
  
## <a name="requirements"></a>Requisitos  
 El objeto WinRTError solo se admite en aplicaciones de la [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)], no en Internet Explorer.  
  
## <a name="see-also"></a>Vea también  
 [Error (Objeto)](../../javascript/reference/error-object-javascript.md)