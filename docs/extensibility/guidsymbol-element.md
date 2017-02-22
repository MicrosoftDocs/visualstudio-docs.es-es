---
title: "Elemento GuidSymbol | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Elementos de esquema XML VSCT, GuidSymbol"
  - "Elemento GuidSymbol (esquema VSCT XML)"
ms.assetid: 11fb3545-8974-4776-9a54-6b6e7739ae31
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# Elemento GuidSymbol
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El `GuidSymbol` elemento contiene el GUID del par GUID:ID que representa un menú, un grupo o un comando. El identificador proviene de un `IDSymbol` elemento en el `GuidSymbol` elemento. El `GuidSymbol` elemento tiene un `name` atributo que proporciona un nombre descriptivo para el GUID, que se encuentra en la `value` atributo.  
  
## Sintaxis  
  
```  
<GuidSymbol name="guidMyCommandSet" value="{xxxxxxxxxxxxx-xxxx-xxxx-xxxxxxxxxxxx}">  
  <IDSymbol>... </IDSymbol>  
  <IDSymbol>... </IDSymbol>  
</GuidSymbol>  
```  
  
## Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### Atributos  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|name|Obligatorio. Nombre del símbolo GUID.|  
|valor|Obligatorio. GUID del símbolo GUID.|  
  
### Elementos secundarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[Elemento IDSymbol](../extensibility/idsymbol-element.md)|Contiene el identificador del par GUID:ID que representa un menú, un grupo o un comando.|  
  
### Elementos primarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[Elemento de símbolos](../extensibility/symbols-element.md)|Grupos de `GuidSymbol` elementos en un archivo de vsct.|  
  
## Comentarios  
 Normalmente, un archivo .vsct contiene tres `GuidSymbol` elementos en su `Symbols` sección, uno para el paquete, uno para el conjunto de comandos \(la colección de menús, grupos y comandos que pone a disposición del paquete\) y otro para los mapas de bits que proporcionan iconos de botones y otros componentes visuales. Cada `IDSymbol` elemento en un determinado `GuidSymbol` elemento debe tener un único `value`. Sin embargo, `IDSymbol` los elementos que tienen valores idénticos pueden existir en un paquete como tienen diferentes objetos primarios.  
  
## Vea también  
 [Tabla de comandos de Visual Studio \(. Archivos de Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)