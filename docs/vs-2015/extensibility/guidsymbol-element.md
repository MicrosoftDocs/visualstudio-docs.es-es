---
title: GuidSymbol (elemento) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, GuidSymbol
- GuidSymbol element (VSCT XML schema)
ms.assetid: 11fb3545-8974-4776-9a54-6b6e7739ae31
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5f11ed48d9dcf961228957cf15db3815c00d14d7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204224"
---
# <a name="guidsymbol-element"></a>GuidSymbol (Elemento)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El `GuidSymbol` elemento contiene el GUID del par GUID: ID que representa un menú, grupo o comando. El Id. de procede de un `IDSymbol` elemento en el `GuidSymbol` elemento. El `GuidSymbol` elemento tiene un `name` atributo que proporciona un nombre descriptivo para el GUID, que se encuentra en la `value` atributo.  
  
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
  
|Atributo|DESCRIPCIÓN|  
|---------------|-----------------|  
|Nombre|Necesario. Nombre del símbolo GUID.|  
|valor|Necesario. GUID del símbolo GUID.|  
  
### <a name="child-elements"></a>Elementos secundarios  
  
|Elemento|DESCRIPCIÓN|  
|-------------|-----------------|  
|[IDSymbol (Elemento)](../extensibility/idsymbol-element.md)|Contiene el identificador del par GUID: ID que representa un menú, grupo o comando.|  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|DESCRIPCIÓN|  
|-------------|-----------------|  
|[Symbols (Elemento)](../extensibility/symbols-element.md)|Grupos `GuidSymbol` elementos en un archivo .vsct.|  
  
## <a name="remarks"></a>Comentarios  
 Normalmente, un archivo .vsct contiene tres `GuidSymbol` elementos en su `Symbols` sección, uno para el propio paquete, uno para el conjunto de comandos (la colección de menús, grupos y comandos que pone a disposición del paquete) y otro para los mapas de bits que proporcionan iconos de los botones y otros componentes visuales. Cada `IDSymbol` elemento en un determinado `GuidSymbol` elemento debe tener un único `value`. Sin embargo, `IDSymbol` los elementos que tienen valores idénticos pueden existir en un paquete, siempre y cuando tengan que diferentes objetos primarios.  
  
## <a name="see-also"></a>Vea también  
 [Archivos de tabla de comandos de Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
