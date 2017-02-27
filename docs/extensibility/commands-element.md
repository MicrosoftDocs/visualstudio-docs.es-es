---
title: "Elemento Commands | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Commands"
helpviewer_keywords: 
  - "Elemento Commands (esquema VSCT XML)"
  - "Elementos de esquema XML VSCT, comandos"
ms.assetid: 47cf16a5-d78b-452e-86f6-b5893856dddf
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# Elemento Commands
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Representa la colección de comandos en la barra de herramientas de VSPackage. La colección puede tener hasta cinco subsecciones, como sigue: menús, grupos, botones, combinaciones y mapas de bits.  
  
 Cada subsección elemento secundario, por ejemplo, \< menú \>, se identifica mediante un identificador de comando único que es un GUID y un par de identificador numérico. El GUID identifica el conjunto de comandos"" y se utiliza para agrupar los comandos relacionados lógicamente. El VSPackage debe definir su propio comando para evitar conflictos con los identificadores de comando que se definen mediante otras VSPackages.  
  
## Sintaxis  
  
```  
<Commands package="GuidMyPackage" >  
  <Menus>... </Menus>  
  <Groups>... </Groups>  
  <Buttons>... </Buttons>  
  <Combos>... </Combos>  
  <Bitmaps>... </Bitmaps>  
</Commands>  
```  
  
## Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### Atributos  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|paquete|Un GUID que identifica el paquete VSPackage que proporciona los comandos.<br /><br /> Por ejemplo, empaquetar \= "guidVsPackage1Pkg".|  
  
### Elementos secundarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[Elemento de menús](../extensibility/menus-element.md)|Define todos los menús que implementa un VSPackage.|  
|[Elemento Groups](../extensibility/groups-element.md)|Contiene entradas que definen los grupos de comando en un VSPackage.|  
|[Elemento de botones](../extensibility/buttons-element.md)|Agrupa los elementos de botón.|  
|[Elemento de mapas de bits](../extensibility/bitmaps-element.md)|Agrupa elementos de mapa de bits.|  
|[Elemento de cuadro combinado](../extensibility/combos-element.md)|Agrupa los elementos del cuadro combinado.|  
  
### Elementos primarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Define todos los elementos que representan los comandos que proporciona un paquete VSPackage al IDE. Posibles elementos son elementos de menú, menús, barras de herramientas y cuadros combinados.|  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar un [Commands Element](../extensibility/commands-element.md).  
  
```  
<Commands package="guidMyPackage"> <Menus> <Menu Condition="'%(DEBUG)' != 'true'" guid="cmdSetGuidMyProductCommands" id="menuIDMainMenu" priority="0x0000" type="Menu"> <Annotation> <Documentation>this is an annotation</Documentation> <AppInfo> <CustomData> <CustomSubElement>Some data</CustomSubElement> </CustomData> </AppInfo> </Annotation> <CommandFlag>AlwaysCreate</CommandFlag> <Strings> <ButtonText>MainMenu</ButtonText> </Strings> </Menu> </Menus> <Commands>  
```  
  
## Vea también  
 [Cómo VSPackages agregar elementos de la interfaz de usuario](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Barras de herramientas, menús y comandos](../extensibility/internals/commands-menus-and-toolbars.md)