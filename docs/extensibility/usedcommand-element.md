---
title: "Elemento UsedCommand | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Elemento UsedCommands (esquema VSCT XML)"
  - "Elementos de esquema XML VSCT, UsedCommands"
ms.assetid: 99cd05d3-644a-42ff-b289-8458cd1b20c0
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# Elemento UsedCommand
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Permite un VSPackage tener acceso a un comando que se define en otro archivo de vsct. Por ejemplo, si su VSPackage utiliza la norma **copia** comando, que se define mediante el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] shell, puede agregar el comando a un menú o barra de herramientas sin necesidad de volver a implementarlo.  
  
## Sintaxis  
  
```  
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />  
```  
  
## Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### Atributos  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|GUID|Obligatorio. El GUID del par de identificador GUID que identifica el comando.|  
|id|Obligatorio. Id. del par de identificador GUID que identifica el comando.|  
|Condición|Opcional. Vea [Atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### Elementos secundarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|Ninguna||  
  
### Elementos primarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[Elemento UsedCommands](../extensibility/usedcommands-element.md)|Elementos de grupos de UsedCommand y otras agrupaciones de UsedCommands.|  
  
## Comentarios  
 Agregando un comando para el `<UsedCommands>` informa de un VSPackage de elemento, el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que el VSPackage requiere que el comando del entorno. Debe agregar una `<UsedCommand>` \(elemento\) para cualquier comando que necesita el paquete no puede incluirse en todas las versiones y configuraciones de Visual Studio. Por ejemplo, si el paquete llama a un comando específico de Visual C\+\+, el comando no estará disponible para los usuarios de Visual Web Developer a menos que incluya un `<UsedCommand>` \(elemento\) para el comando.  
  
## Ejemplo  
  
```  
<UsedCommands> <UsedCommand guid="guidVSStd97" id="cmdidCut"/> <UsedCommand guid="guidVSStd97" id="cmdidCopy"/> <UsedCommand guid="guidVSStd97" id="cmdidPaste"/> </UsedCommands>  
```  
  
## Vea también  
 [Elemento UsedCommands](../extensibility/usedcommands-element.md)   
 [Tabla de comandos de Visual Studio \(. Archivos de Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)