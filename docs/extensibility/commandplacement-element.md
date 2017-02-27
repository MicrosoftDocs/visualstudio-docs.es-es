---
title: "Elemento CommandPlacement | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Elemento CommandPlacements (esquema VSCT XML)"
  - "Elementos de esquema XML VSCT, CommandPlacements"
ms.assetid: 2cbd7ac8-c55a-43d8-a26d-713b3d790016
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# Elemento CommandPlacement
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El elemento CommandPlacement permite botones, grupos y menús que se incluirán en más de un grupo o un menú. Mediante el elemento de CommandPlacement, es necesario volver a definir completamente estos elementos con el fin de modificar la apariencia de una interfaz de usuario.  
  
 Para obtener más información, consulta [Creación de grupos reutilizables de botones](../extensibility/creating-reusable-groups-of-buttons.md).  
  
## Sintaxis  
  
```  
<CommandPlacement guid=guidMyCommandSet" id="MyCommand" priority="0x001" >  
  <Parent>... </Parent>  
</CommandPlacement>  
```  
  
## Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### Atributos  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|GUID|Obligatorio. El guid del conjunto de comandos, como se define en el [Elemento de símbolos](../extensibility/symbols-element.md).|  
|id|Obligatorio. El identificador del menú, el grupo o el comando colocar, como se define en el `Symbols Element`.|  
|priority|Obligatorio. Determina la posición del elemento visual de su elemento primario.|  
|Condición|Opcional. Vea [Atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### Elementos secundarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|Elemento primario|Obligatorio. El menú o el grupo que hospeda el elemento que se va a colocar.|  
  
### Elementos primarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[Elemento CommandPlacements](../extensibility/commandplacements-element.md)|Especifica los grupos de elementos CommandPlacements y CommandPlacement.|  
  
## Ejemplo  
  
```  
<CommandPlacements> <CommandPlacement guid="guidWidgetPackage" id="cmdidInsertOptions" priority="0x0300"> <Parent guid="cmdGuidWidgetCommands" id="menuIDEditWidget"/> </CommandPlacement> </CommandPlacements>  
```  
  
## Vea también  
 [Elemento CommandPlacements](../extensibility/commandplacements-element.md)   
 [Tabla de comandos de Visual Studio \(. Archivos de Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)