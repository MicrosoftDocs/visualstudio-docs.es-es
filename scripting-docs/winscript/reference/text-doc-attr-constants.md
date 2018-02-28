---
title: Constantes TEXT_DOC_ATTR | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- TEXT_DOC_ATTR
apilocation:
- scrobj.dll
helpviewer_keywords:
- TEXT_DOC_ATTR constants
ms.assetid: fd9c53a4-8f73-4c6a-abe5-6b831ecd5b1e
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 130895e0e70b1044fab5d5ab406f940b036c37f0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="textdocattr-constants"></a>Constantes TEXT_DOC_ATTR
Describen los atributos del documento.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
typedef DWORD TEXT_DOC_ATTR;  
```  
  
## <a name="constants"></a>Constantes  
  
|Constante|Valor|Descripción|  
|--------------|-----------|-----------------|  
|TEXT_DOC_ATTR_READONLY|0x00000001|El documento es de solo lectura.|  
|TEXT_DOC_ATTR_TYPE_PRIMARY|0x00000002|El documento es el archivo principal de este árbol de documentos.|  
|TEXT_DOC_ATTR_TYPE_WORKER|0x00000004|El documento es un trabajador.|  
|TEXT_DOC_ATTR_TYPE_SCRIPT|0x00000008|El documento es un archivo de script.|  
  
## <a name="see-also"></a>Vea también  
 [Active Script Debugger (Constantes, Enumeraciones y Estructuras)](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)