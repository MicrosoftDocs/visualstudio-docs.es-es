---
title: "Elemento VisibilityConstraints | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VisibilityConstraints"
helpviewer_keywords: 
  - "Elementos de esquema XML VSCT, VisibilityConstraints"
  - "Elemento VisibilityConstraints (esquema VSCT XML)"
ms.assetid: d6dcd314-6fe4-4693-a189-91fa026c7b34
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# Elemento VisibilityConstraints
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El elemento de VisibilityConstraints determina la visibilidad de los grupos de barras de herramientas y comandos estática. La visibilidad en primer lugar se controla mediante el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] el entorno de desarrollo integrado \(IDE\) sin necesidad de cargar el VSPackage.  
  
## Sintaxis  
  
```  
<VisibilityConstraints>  
  <VisibilityConstraint>... </VisibilityConstraint>  
  <VisibilityConstraint>... </VisibilityConstraint>  
</VisibilityConstraint>  
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
|[Elemento VisibilityItem](../extensibility/visibilityitem-element.md)|Determina la visibilidad de los comandos y las barras de herramientas estática.|  
|[VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|Determina la visibilidad de los grupos de barras de herramientas y comandos estática.|  
  
### Elementos primarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Define todos los elementos que representan los comandos \(por ejemplo, elementos de menú, menús, barras de herramientas y cuadros combinados\) proporciona un VSPackage al IDE.|  
  
## Ejemplo  
  
```  
<VisibilityConstraints> <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget" context="guidNotViewSourceMode"/> </VisibilityConstraints>  
```  
  
## Vea también  
 [Elemento VisibilityItem](../extensibility/visibilityitem-element.md)   
 [Tabla de comandos de Visual Studio \(. Archivos de Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)