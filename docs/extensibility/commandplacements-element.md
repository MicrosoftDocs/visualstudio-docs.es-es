---
title: "Elemento CommandPlacements | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CommandPlacements"
helpviewer_keywords: 
  - "Elemento CommandPlacements (esquema VSCT XML)"
  - "Elementos de esquema XML VSCT, CommandPlacements"
ms.assetid: 78a5724a-3b9f-4c78-9c0d-8faa3924f81c
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Elemento CommandPlacements
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El elemento CommandPlacements agrupa elementos CommandPlacement y otras agrupaciones de CommandPlacements.  
  
 El elemento CommandPlacements es opcional. Si no hay comandos, grupos o menús deben incluirse en una ubicación secundaria, no es necesario incluir esta sección en el archivo .vsct.  
  
## Sintaxis  
  
```  
<CommandPlacements>  
  <CommandPlacement>... </CommandPlacement>  
  <CommandPlacement>... </CommandPlacement>  
</CommandPlacements>  
```  
  
## Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### Atributos  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|Condición|Opcional. Vea [Atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### Elementos secundarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|CommandPlacements|Elementos de grupos de CommandPlacement y otras agrupaciones de CommandPlacements.|  
|[Elemento CommandPlacement](../extensibility/commandplacement-element.md)|Habilita los botones, grupos y menús que se incluirán en más de un grupo o un menú.|  
  
### Elementos primarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Define todos los elementos que representan comandos.|  
  
## Ejemplo  
  
```  
<CommandPlacements> <CommandPlacement guid="guidWidgetPackage" id="cmdidInsertOptions" priority="0x0300"> <Parent guid="cmdGuidWidgetCommands" id="menuIDEditWidget"/> </CommandPlacement> </CommandPlacements>  
```  
  
## Vea también  
 [Elemento CommandPlacement](../extensibility/commandplacement-element.md)   
 [Tabla de comandos de Visual Studio \(. Archivos de Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)