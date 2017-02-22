---
title: "Elemento IDSymbol | Microsoft Docs"
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
  - "Elemento IDSymbol (esquema VSCT XML)"
  - "Elementos de esquema XML VSCT, IDSymbol"
ms.assetid: 760cfd20-3c06-422c-9103-98bfa1f387f8
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# Elemento IDSymbol
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El `IDSymbol` elemento contiene el identificador del par GUID:ID que representa un menú, un grupo o un comando. Incluye el GUID del primario `GuidSymbol` elemento. El `IDSymbol` elemento tiene un `name` atributo que proporciona un nombre descriptivo para el identificador, que se encuentra en la `value` atributo.  
  
## Sintaxis  
  
```  
<IDSymbol name=ElementName value="0x0010" />  
```  
  
## Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### Atributos  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|name|Obligatorio. Nombre del símbolo de ID.|  
|valor|Obligatorio. Valor de identificador numérico del símbolo de ID.|  
  
### Elementos secundarios  
 Ninguno.  
  
### Elementos primarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[Elemento GuidSymbol](../extensibility/guidsymbol-element.md)|Contiene el GUID del par GUID:ID que representa un menú, un grupo o un comando. Agrupa los elementos `IDSymbol`.|  
  
## Comentarios  
 Cada `IDSymbol` elemento en un determinado `GuidSymbol` elemento debe tener un único `value`. Sin embargo, `IDSymbol` los elementos que tienen valores idénticos pueden existir en un paquete como tienen diferentes objetos primarios.  
  
## Vea también  
 [Tabla de comandos de Visual Studio \(. Archivos de Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)