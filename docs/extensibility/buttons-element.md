---
title: "Elemento de botones | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Elemento de botones (esquema VSCT XML)"
  - "Elementos de esquema XML VSCT, botones"
ms.assetid: 9f2cf94d-dec5-4776-a836-9a89c75f0c87
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Elemento de botones
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Grupos [botón](../extensibility/button-element.md) elementos que representan los comandos individuales.  
  
## Sintaxis  
  
```  
<Buttons>  
  <Button>... </Button>  
  <Button>... </Button>  
</Buttons>  
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
|[Buttons Element](../extensibility/buttons-element.md)|Agrupa los elementos de botón.|  
|[Elemento Button](../extensibility/button-element.md)|Define un comando que el usuario puede interactuar con.|  
  
### Elementos primarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[Elemento Commands](../extensibility/commands-element.md)|Representa la colección de comandos en la barra de herramientas de VSPackage.|  
  
## Ejemplo  
  
```  
<Buttons> <Button guid="guidMenuAndCommandsCmdSet" id="cmdidMyCommand"     priority="0x100" type="Button"> <Parent guid="guidMenuAndCommandsCmdSet" id="MyMenuGroup"/> <Icon guid="guidGenericCmdBmp" id="bmpArrow"/> <Strings> <ButtonText>C# Command Sample</ButtonText> </Strings> </Button> </Buttons>  
```  
  
## Vea también  
 [Cómo VSPackages agregar elementos de la interfaz de usuario](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Barras de herramientas, menús y comandos](../extensibility/internals/commands-menus-and-toolbars.md)