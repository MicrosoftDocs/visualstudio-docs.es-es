---
title: IDSymbol (elemento) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDSymbol element (VSCT XML schema)
- VSCT XML schema elements, IDSymbol
ms.assetid: 760cfd20-3c06-422c-9103-98bfa1f387f8
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3b4876144093d5e937a194095af1b128dc3efabd
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49253050"
---
# <a name="idsymbol-element"></a>IDSymbol (Elemento)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
|value|Requerido. Valor de identificador numérico del símbolo de identificador.|  
  
### <a name="child-elements"></a>Elementos secundarios  
 Ninguno.  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[GuidSymbol (Elemento)](../extensibility/guidsymbol-element.md)|Contiene el GUID del par GUID: ID que representa un menú, grupo o comando. Agrupa los elementos `IDSymbol`.|  
  
## <a name="remarks"></a>Comentarios  
 Cada `IDSymbol` elemento en un determinado `GuidSymbol` elemento debe tener un único `value`. Sin embargo, `IDSymbol` los elementos que tienen valores idénticos pueden existir en un paquete, siempre y cuando tengan que diferentes objetos primarios.  
  
## <a name="see-also"></a>Vea también  
 [Archivos de tabla de comandos de Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

