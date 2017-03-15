---
title: "Elemento include | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Include"
helpviewer_keywords: 
  - "Incluir el elemento (esquema VSCT XML)"
  - "Elementos de esquema XML VSCT, incluir"
ms.assetid: c923dfe6-084a-4105-aec1-f0a3f8399c54
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# Elemento include
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El elemento Include especifica un archivo que se encuentra en proporcionado, incluya la ruta de acceso para la inserción en el archivo actual.  Todos los símbolos y tipos definidos formarán parte del resultado compilado.  
  
## Sintaxis  
  
```c#  
<Include href="stdidcmd.h" />  
```  
  
## Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### Atributos  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|href|Obligatorio. La ruta de acceso al archivo de encabezado:<br /><br /> href\="stdidcmd.h"|  
|Condición|Opcional. Vea [Atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### Elementos secundarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|Ninguno.|Ninguno.|  
  
### Elementos primarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Define todos los elementos que representan comandos, es decir, elementos de menú, menús, barras de herramientas y cuadros combinados, que proporciona un paquete VSPackage al IDE.|  
  
## Ejemplo  
  
```  
<Include href="PackagePlacements.vsct"/>  
```  
  
## Vea también  
 [Tabla de comandos de Visual Studio \(. Archivos de Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)