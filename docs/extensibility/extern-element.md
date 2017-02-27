---
title: "Elemento extern | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Extern"
helpviewer_keywords: 
  - "Elementos de esquema XML VSCT, Extern"
  - "Elemento extern (esquema VSCT XML)"
ms.assetid: db6c3ddd-a1ba-450a-897a-bb568a5377fc
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# Elemento extern
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El elemento externo hace referencia a los archivos externos de encabezado \(. h\) que se combina con el archivo .vsct en tiempo de compilación. Los archivos a combinarse deben estar en la ruta de acceso de inclusión indica al compilador VSCT o hace referencia a un [Elemento include](../extensibility/include-element.md). Los archivos pueden ser otros archivos .vsct o los archivos de encabezado de C\+\+.  
  
 Definiciones en archivos de encabezado deben tener el formato "\#define \[símbolo\] \[valor\]" el valor puede ser otro símbolo si se ha definido previamente. Las definiciones se pueden utilizar en instrucciones condicionales de elementos del comando. Se descartará cualquier símbolo no utilizada realmente.  
  
 CommandTable Element  
Extern Element  
  
## Sintaxis  
  
```  
<Extern href="stdidcmd.h" />  
```  
  
## Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### Atributos  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|href|Obligatorio. La ruta de acceso al archivo de encabezado:<br /><br /> href\="stdidcmd.h"|  
|Condición|Opcional. Vea [Atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
|lenguaje|Opcional. El idioma predeterminado de todos los [\< cadenas \>](../extensibility/strings-element.md) elementos en la tabla de comandos:<br /><br /> Language \= "en\-us"|  
  
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
<?xml version="1.0" encoding="utf-8"?> <CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10- 18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema"> <Extern href="C:\VSCore\vscommon\inc\vsshlids.h"/> … <Commands package="guidMyPackage"> </CommandTable>  
```  
  
## Vea también  
 [Tabla de comandos de Visual Studio \(. Archivos de Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Cómo VSPackages agregar elementos de la interfaz de usuario](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Barras de herramientas, menús y comandos](../extensibility/internals/commands-menus-and-toolbars.md)