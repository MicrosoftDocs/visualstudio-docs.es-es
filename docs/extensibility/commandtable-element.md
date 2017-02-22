---
title: "Elemento CommandTable | Microsoft Docs"
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
  - "CommandTable"
helpviewer_keywords: 
  - "Elemento CommandTable (esquema VSCT XML)"
  - "Elementos de esquema XML VSCT, CommandTable"
ms.assetid: 15c38159-660a-4ef4-9643-aa6fcfca82a9
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# Elemento CommandTable
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

CommandTable es el elemento raíz del archivo vsct. Este es el archivo que define el diseño real y el tipo de los comandos que proporciona un paquete VSPackage al IDE. Comandos pueden incluir elementos de menú, menús, barras de herramientas y cuadros combinados. Para obtener más información, consulta [Tabla de comandos de Visual Studio \(. Archivos de Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## Sintaxis  
  
```  
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema" >  
  <Extern>... </Extern>  
  <Include>... </Include>  
  <Define>... </Define>  
  <Commands>... </Commands>  
  <CommandPlacements>... </CommandPlacements>  
  <VisibilityConstraints>... </VisibilityConstraints>  
  <KeyBindings>... </KeyBindings>  
  <UsedCommands... </UsedCommands>  
  <Symbols>... </Symbols>  
</CommandTable>  
```  
  
## Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### Atributos  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|xmlns|Obligatorio. Espacios de nombres XML:<br /><br /> xmlns \= "http:\/\/schemas.microsoft.com\/VisualStudio\/2005\-10\-18\/CommandTable"<br /><br /> xmlns: xs \= "http:\/\/www.w3.org\/2001\/XMLSchema"|  
|lenguaje|Opcional. El atributo language se puede utilizar para especificar el idioma predeterminado de todos los elementos de \< cadenas \> en la tabla de comandos.  Si no se especifica el idioma, se utilizará el idioma del proceso actual:<br /><br /> Language \= "en\-us"|  
  
### Elementos secundarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[Elemento extern](../extensibility/extern-element.md)|Opcional. Contiene directivas de preprocesador para el compilador.|  
|[Elemento include](../extensibility/include-element.md)|Opcional. Contiene las rutas de acceso a los archivos que se incluyen en la compilación.|  
|[Definir el elemento](../extensibility/define-element.md)|Opcional. Define un símbolo de su nombre y valor.|  
|[Elemento Commands](../extensibility/commands-element.md)|Opcional. El elemento primario define todos los comandos para el paquete VSPackage que contiene todos los demás elementos.|  
|[Elemento CommandPlacements](../extensibility/commandplacements-element.md)|Opcional. Define dónde en la barra de comandos, los comandos son colocar.|  
|[Elemento VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|Opcional. Determina la visibilidad de los comandos y las barras de herramientas estática.|  
|[Elemento de enlaces de teclado](../extensibility/keybindings-element.md)|Opcional. Especifica las combinaciones de teclas de método abreviado, si existe, para los comandos.|  
|[Elemento UsedCommands](../extensibility/usedcommands-element.md)|Opcional. Permite un VSPackage, opcionalmente, implementar su propia versión de funcionalidad admitida originalmente por otros VSPackages.|  
|[Symbols Element](http://msdn.microsoft.com/es-es/f2ddd0aa-c3dd-439e-834d-28f136a27ffa)|Opcional. Contiene los datos de símbolos\-\-GUID, identificadores etc., para que el compilador.|  
  
### Elementos primarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|Ninguno||  
  
## Vea también  
 [Tabla de comandos de Visual Studio \(. Archivos de Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)