---
title: "Elemento Parent | Microsoft Docs"
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
  - "Elementos de esquema XML VSCT, primario"
  - "Elemento primario (esquema VSCT XML)"
ms.assetid: e4624ac8-1b9a-4940-910a-528a661cefad
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# Elemento Parent
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El elemento primario de un cuadro combinado o botón sólo puede ser un grupo. El elemento primario de un menú o un grupo puede ser cualquier otro menú o grupo. En un [Elemento CommandPlacement](../extensibility/commandplacement-element.md), este elemento es necesario; en todas las demás instancias es opcional. Si se omite este elemento, el elemento primario de `Group_Undefined:0` se que implica.  
  
## Sintaxis  
  
```  
<Parent guid="guidMyCommandSet" id="MyParentGroupOrMenu" />  
```  
  
## Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### Atributos  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|GUID|Obligatorio. Identificador GUID de GUID o Id. del comando.|  
|id|Obligatorio. Identificador de comando del identificador de GUID o ID.|  
  
### Elementos secundarios  
 Ninguna  
  
### Elementos primarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Define todos los elementos que representan los comandos que proporciona un VSPackage en el entorno de desarrollo integrado \(IDE\). Por ejemplo, elementos de menú, menús, barras de herramientas y cuadros combinados.|  
|[Elemento de botones](../extensibility/buttons-element.md)|Agrupa los elementos [Elemento Button](../extensibility/button-element.md).|  
|[Elemento de menús](../extensibility/menus-element.md)|Define todos los menús que implementa un VSPackage.|  
|[Elemento Groups](../extensibility/groups-element.md)|Contiene entradas que definen los grupos de comandos de un paquete VSPackage.|  
  
## Vea también  
 [Tabla de comandos de Visual Studio \(. Archivos de Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)