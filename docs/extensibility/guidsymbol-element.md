---
title: Elemento GuidSymbol | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, GuidSymbol
- GuidSymbol element (VSCT XML schema)
ms.assetid: 11fb3545-8974-4776-9a54-6b6e7739ae31
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6d5e3a3f4d33e166d344669dbeb4bc1a877335f0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="guidsymbol-element"></a>Elemento GuidSymbol
El `GuidSymbol` elemento contiene el GUID del par GUID: ID que representa un menú, grupo o comando. El identificador procede de un `IDSymbol` elemento en el `GuidSymbol` elemento. El `GuidSymbol` elemento tiene un `name` atributo que proporciona un nombre descriptivo para el GUID, que se encuentra en la `value` atributo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<GuidSymbol name="guidMyCommandSet" value="{xxxxxxxxxxxxx-xxxx-xxxx-xxxxxxxxxxxx}">  
  <IDSymbol>... </IDSymbol>  
  <IDSymbol>... </IDSymbol>  
</GuidSymbol>  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|name|Requerido. Nombre del símbolo GUID.|  
|value|Requerido. GUID del símbolo GUID.|  
  
### <a name="child-elements"></a>Elementos secundarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[IDSymbol (Elemento)](../extensibility/idsymbol-element.md)|Contiene el identificador del par GUID: ID que representa un menú, grupo o comando.|  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[Symbols (Elemento)](../extensibility/symbols-element.md)|Grupos de `GuidSymbol` elementos en un archivo .vsct.|  
  
## <a name="remarks"></a>Comentarios  
 Normalmente, un archivo .vsct contiene tres `GuidSymbol` elementos en su `Symbols` sección, uno para el propio paquete, uno para el conjunto de comandos (la colección de menús, los grupos y los comandos que pone a disposición del paquete) y otro para los mapas de bits que proporcionan iconos de los botones y otros componentes visuales. Cada `IDSymbol` elemento en un determinado `GuidSymbol` debe tener un único elemento `value`. Sin embargo, `IDSymbol` elementos que tengan valores idénticos pueden existir en un paquete como tienen diferentes objetos primarios.  
  
## <a name="see-also"></a>Vea también  
 [Archivos de tabla de comandos de Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)