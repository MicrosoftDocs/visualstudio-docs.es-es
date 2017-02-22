---
title: "Definir el elemento | Microsoft Docs"
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
  - "Elementos de esquema XML VSCT, definir"
  - "Definir el elemento (esquema VSCT XML)"
ms.assetid: 5aee74e3-de41-4dc6-9618-93e158af56dd
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# Definir el elemento
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Define un par de nombre y valor de símbolo. Este símbolo se puede evaluar mediante atributos condicionales. Para obtener más información, consulta [Atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md). Vea también el [Elemento de símbolos](../extensibility/symbols-element.md).  
  
## Sintaxis  
  
```  
<Define name="Mode" value="Standard" />  
```  
  
## Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### Atributos  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|name|Obligatorio. El nombre del símbolo:<br /><br /> nombre \= "Mode"|  
|valor|Obligatorio. El valor del símbolo:<br /><br /> valor \= "Estándar"|  
|Condición|Opcional. Para obtener más información, consulta [Atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### Elementos secundarios  
 Ninguno.  
  
### Elementos primarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Define todos los elementos que representan los comandos que proporciona un VSPackage en el entorno de desarrollo integrado \(IDE\). Por ejemplo, elementos de menú, menús, barras de herramientas y cuadros combinados.|  
  
## Ejemplo  
  
```  
<Define name="DEMO_UI"/> <Define name="MODE" value="Standard"/>  
```  
  
## Vea también  
 [Tabla de comandos de Visual Studio \(. Archivos de Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)