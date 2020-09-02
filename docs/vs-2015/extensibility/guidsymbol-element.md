---
title: Elemento GuidSymbol | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204224"
---
# <a name="guidsymbol-element"></a>GuidSymbol (Elemento)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El `GuidSymbol` elemento contiene el GUID del par GUID: ID que representa un menú, un grupo o un comando. El identificador procede de un `IDSymbol` elemento del `GuidSymbol` elemento. El `GuidSymbol` elemento tiene un `name` atributo que proporciona un nombre descriptivo para el GUID, que se encuentra en el `value` atributo.  
  
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
|name|Necesario. Nombre del símbolo GUID.|  
|value|Necesario. GUID del símbolo GUID.|  
  
### <a name="child-elements"></a>Elementos secundarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[IDSymbol (Elemento)](../extensibility/idsymbol-element.md)|Contiene el identificador del par GUID: ID que representa un menú, grupo o comando.|  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[Symbols (Elemento)](../extensibility/symbols-element.md)|Agrupa `GuidSymbol` los elementos de un archivo. Vsct.|  
  
## <a name="remarks"></a>Observaciones  
 Normalmente, un archivo. Vsct contiene tres `GuidSymbol` elementos en su `Symbols` sección, uno para el propio paquete, uno para el conjunto de comandos (la colección de menús, grupos y comandos que el paquete pone a disposición) y otro para los mapas de bits que proporcionan iconos para botones y otros componentes visuales. Cada `IDSymbol` elemento de un `GuidSymbol` elemento determinado debe tener un único `value` . Sin embargo, `IDSymbol` los elementos que tienen valores idénticos pueden existir en un paquete siempre que tengan distintos elementos primarios.  
  
## <a name="see-also"></a>Consulte también  
 [Archivos de tabla de comandos de Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
