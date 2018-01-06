---
title: Elemento IDSymbol | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDSymbol element (VSCT XML schema)
- VSCT XML schema elements, IDSymbol
ms.assetid: 760cfd20-3c06-422c-9103-98bfa1f387f8
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 004b40acb50fe85604d0a3cfa9f5626891fa66a4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idsymbol-element"></a>Elemento IDSymbol
El `IDSymbol` elemento contiene el identificador del par GUID: ID que representa un menú, grupo o comando. Incluye el GUID del elemento primario `GuidSymbol` elemento. El `IDSymbol` elemento tiene un `name` atributo que proporciona un nombre descriptivo para el identificador, que se encuentra en la `value` atributo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<IDSymbol name=ElementName value="0x0010" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|name|Requerido. Nombre del símbolo de identificador.|  
|value|Requerido. Valor de Id. numérico del símbolo de identificador.|  
  
### <a name="child-elements"></a>Elementos secundarios  
 Ninguno.  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[GuidSymbol (Elemento)](../extensibility/guidsymbol-element.md)|Contiene el GUID del par GUID: ID que representa un menú, grupo o comando. Agrupa los elementos `IDSymbol`.|  
  
## <a name="remarks"></a>Comentarios  
 Cada `IDSymbol` elemento en un determinado `GuidSymbol` debe tener un único elemento `value`. Sin embargo, `IDSymbol` elementos que tengan valores idénticos pueden existir en un paquete como tienen diferentes objetos primarios.  
  
## <a name="see-also"></a>Vea también  
 [Archivos de tabla de comandos de Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)