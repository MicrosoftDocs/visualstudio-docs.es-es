---
title: FunctionArgType | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- FunctionArgType symbol
ms.assetid: 9f072fd3-0b99-405c-af99-fd44cd56fd73
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 96f816ff40b40f0de6b6f828996a64407b88f04e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58997426"
---
# <a name="functionargtype"></a>FunctionArgType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Cada parámetro de una función se identifica mediante un `SymTagFunctionArgType` símbolos.  
  
## <a name="properties"></a>Propiedades  
 La siguiente tabla muestra propiedades adicionales de válido para este tipo de símbolo.  
  
|Property|Tipo de datos|Descripción|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|`IDiaSymbol*`|Símbolo de FunctionType primario.|  
|[IDiaSymbol::get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|`DWORD`|Id. del símbolo de clase primaria.|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Símbolo de la envolvente [Compiland](../../debugger/debug-interface-access/compiland.md).|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Id. del símbolo léxico primario.|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Id. de índice de símbolo.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Devuelve `SymTagFunctionArgType` (uno de los [SymTagEnum (enumeración)](../../debugger/debug-interface-access/symtagenum.md) valores).|  
|[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|Tipo del parámetro.|  
|[IDiaSymbol::get_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|Id. del símbolo de tipo.|  
  
## <a name="see-also"></a>Vea también  
 [Jerarquía de clases de tipos de símbolos](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)   
 [FunctionType](../../debugger/debug-interface-access/functiontype.md)
