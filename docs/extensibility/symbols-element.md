---
title: "Elemento de s&#237;mbolos | Microsoft Docs"
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
  - "Elemento de símbolos (esquema VSCT XML)"
  - "Elementos de esquema XML VSCT, símbolos"
ms.assetid: 1cda43d8-42a5-4b1b-a3c8-cf0401c3202f
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# Elemento de s&#237;mbolos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Define los GUID e identificadores de otros elementos VSCT. Para código no administrado, esta información normalmente procede de los archivos de encabezado especificados por [Elemento extern](../extensibility/extern-element.md). El código administrado utiliza los elementos secundarios del elemento de símbolos para definir esta información.  
  
 Si crea un archivo de vsct desde un archivo .cto existente, los símbolos se generará como elementos secundarios del elemento de símbolos. Para obtener más información, consulta [Cómo: Crear un archivo .vsct a partir de un archivo .cto existente](../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file.md).  
  
 El elemento de símbolos no debe confundirse con el [Definir el elemento](../extensibility/define-element.md), que define los pares de nombre y valor para su uso por el preprocesador.  
  
## Sintaxis  
  
```  
<Symbols>  
  <GuidSymbol>... </GuidSymbol>  
  <GuidSymbol>... </GuidSymbol>  
</Symbols>  
```  
  
## Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### Atributos  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|Ninguna||  
  
### Elementos secundarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|GuidSymbol|Define un símbolo GUID. GuidSymbol tiene dos atributos necesarios: nombre y valor. El nombre es el nombre del símbolo, y el valor es el valor del GUID como una cadena.<br /><br /> Por ejemplo: \< nombre de GuidSymbol \= "guidVsPackage1Pkg" value \= "{c5f54698\-101a\-4846\-84d3\-dc748f9cd848}" \/ \>|  
|IDSymbol|Define un símbolo. IDSymbol tiene dos atributos necesarios: nombre y valor. El nombre es el nombre del símbolo, y el valor es el valor del símbolo como una cadena.<br /><br /> Por ejemplo: \< nombre de IDSymbol \= "MyMenuGroup" value \= "0x1020" \/ \>|  
  
### Elementos primarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[Elemento CommandTable](../extensibility/commandtable-element.md)|El elemento raíz del archivo vsct.|  
  
## Ejemplo  
  
```  
<Symbols> <GuidSymbol name="guidVsPackage1Pkg" value="{c5f54698-101a-4846-84d3-dc748f9cd848}" /> <GuidSymbol name="guidVsPackage1CmdSet" value="{cb9dfd7f-2fcc-4a3e-aae8-f7fe30b1cfac}"> <IDSymbol name="MyMenuGroup" value="0x1020" /> <IDSymbol name="cmdidMyCommand" value="0x0100" /> <IDSymbol name="cmdidMyTool" value="0x0101" /> </GuidSymbol> </Symbols>  
```  
  
## Vea también  
 [Tabla de comandos de Visual Studio \(. Archivos de Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)