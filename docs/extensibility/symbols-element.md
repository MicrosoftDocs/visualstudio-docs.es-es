---
title: Símbolos elemento | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Symbols element (VSCT XML schema)
- VSCT XML schema elements, Symbols
ms.assetid: 1cda43d8-42a5-4b1b-a3c8-cf0401c3202f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 87e9159e1e392ff242407b105589f4f33341b45b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31142781"
---
# <a name="symbols-element"></a>Elemento de símbolos
Define los GUID e identificadores que son utilizados por otros elementos VSCT. Para código no administrado, esta información normalmente procede de los archivos de encabezado que se especifican mediante [Extern elemento](../extensibility/extern-element.md). El código administrado utiliza los elementos secundarios del elemento de símbolos para definir esta información.  
  
 Si crea un archivo .vsct desde un archivo .cto existente, se generará los símbolos como elementos secundarios del elemento de símbolos. Para obtener más información, vea [Cómo: crear una. Archivo de Vsct desde una existente. Archivo de director de tecnología](../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file).  
  
 El elemento de símbolos no debe confundirse con el [definir elemento](../extensibility/define-element.md), que define los pares de nombre / valor para su uso por el preprocesador.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<Symbols>  
  <GuidSymbol>... </GuidSymbol>  
  <GuidSymbol>... </GuidSymbol>  
</Symbols>  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|Ninguna||  
  
### <a name="child-elements"></a>Elementos secundarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|GuidSymbol|Define un símbolo GUID. GuidSymbol tiene dos atributos obligatorios: nombre y valor. El nombre es el nombre del símbolo y el valor es el valor del GUID como una cadena.<br /><br /> Por ejemplo:\<GuidSymbol name = "guidVsPackage1Pkg" value = "{c5f54698-101a-4846-84d3-dc748f9cd848}" / >|  
|IDSymbol|Define un símbolo. IDSymbol tiene dos atributos obligatorios: nombre y valor. El nombre es el nombre del símbolo y el valor es el valor del símbolo como una cadena.<br /><br /> Por ejemplo:\<IDSymbol name = "MyMenuGroup" value = "0x1020" / >|  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[CommandTable (Elemento)](../extensibility/commandtable-element.md)|El elemento raíz del archivo vsct.|  
  
## <a name="example"></a>Ejemplo  
  
```  
<Symbols>  
  <GuidSymbol name="guidVsPackage1Pkg" value="{c5f54698-101a-4846-84d3-dc748f9cd848}" />  
  <GuidSymbol name="guidVsPackage1CmdSet" value="{cb9dfd7f-2fcc-4a3e-aae8-f7fe30b1cfac}">  
    <IDSymbol name="MyMenuGroup" value="0x1020" />  
    <IDSymbol name="cmdidMyCommand" value="0x0100" />  
    <IDSymbol name="cmdidMyTool" value="0x0101" />  
  </GuidSymbol>  
</Symbols>  
```  
  
## <a name="see-also"></a>Vea también  
 [Archivos de tabla de comandos de Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)