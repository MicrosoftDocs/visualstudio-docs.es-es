---
title: TEXT_DOCUMENT_ARRAY (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- TEXT_DOCUMENT_ARRAY Structure
ms.assetid: 47c08f23-981b-4105-9240-6dfffc6cb91b
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8ff283b52d15310304fb60c322bdb51c33ed33ac
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54344231"
---
# <a name="textdocumentarray-structure"></a>TEXT_DOCUMENT_ARRAY (Estructura)
Una matriz de [IDebugDocumentText (interfaz)](../../winscript/reference/idebugdocumenttext-interface.md) objetos. CoTaskMemAlloc se asignan a los miembros.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
typedef struct tagTEXT_DOCUMENT_ARRAY{    DWORD dwCount;    [size_is(dwCount)] IDebugDocumentText **Members;} TEXT_DOCUMENT_ARRAY;  
```  
  
## <a name="members"></a>Miembros  
 `dwCount`  
 El número de documentos.  
  
 `Members`  
 El conjunto de documentos.  
  
## <a name="see-also"></a>Vea también  
 [Active Script Debugger (Constantes, Enumeraciones y Estructuras)](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)