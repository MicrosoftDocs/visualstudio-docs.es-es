---
title: "Elemento UsedCommands | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "UsedCommands"
helpviewer_keywords: 
  - "Elemento UsedCommands (esquema VSCT XML)"
  - "Elementos de esquema XML VSCT, UsedCommands"
ms.assetid: 5e000ee0-a919-46e9-9277-2a0659f1eb78
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# Elemento UsedCommands
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El elemento UsedCommands agrupa elementos UsedCommand y otras agrupaciones de UsedCommands.  
  
 El elemento UsedCommands es opcional. Si no se llama comandos definidos fuera de su paquete, no es necesario incluir esta sección en el archivo .vsct.  
  
## Sintaxis  
  
```  
<UsedCommands condition="Defined(DEBUG)">  
  <UsedCommand ... />  
</UsedCommands>  
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
|[Elemento UsedCommand](../extensibility/usedcommand-element.md)|El comando es implementado por otro código.|  
  
### Elementos primarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Define todos los elementos que representan comandos \(por ejemplo, elementos de menú, menús, barras de herramientas y cuadros combinados\) que proporciona un VSPackage en el entorno de desarrollo integrado \(IDE\).|  
  
## Ejemplo  
  
```  
<UsedCommands> <UsedCommand guid="guidVSStd97" id="cmdidCut"/> <UsedCommand guid="guidVSStd97" id="cmdidCopy"/> <UsedCommand guid="guidVSStd97" id="cmdidPaste"/> </UsedCommands>  
```  
  
## Vea también  
 [Elemento UsedCommand](../extensibility/usedcommand-element.md)   
 [Tabla de comandos de Visual Studio \(. Archivos de Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)