---
title: TEXT_DOCUMENT_ARRAY (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: TEXT_DOCUMENT_ARRAY Structure
ms.assetid: 47c08f23-981b-4105-9240-6dfffc6cb91b
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 03ed7f13b4e57f9e44ca147810614f980b24b9a5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="textdocumentarray-structure"></a>TEXT_DOCUMENT_ARRAY (Estructura)
Una matriz de [IDebugDocumentText (interfaz)](../../winscript/reference/idebugdocumenttext-interface.md) objetos. Los miembros se asignan con CoTaskMemAlloc.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
typedef struct tagTEXT_DOCUMENT_ARRAY{    DWORD dwCount;    [size_is(dwCount)] IDebugDocumentText **Members;} TEXT_DOCUMENT_ARRAY;  
```  
  
## <a name="members"></a>Miembros  
 `dwCount`  
 El número de documentos.  
  
 `Members`  
 El conjunto de documentos.  
  
## <a name="see-also"></a>Vea también  
 [Active Script Debugger (Constantes, Enumeraciones y Estructuras)](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)