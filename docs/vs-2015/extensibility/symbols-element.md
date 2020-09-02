---
title: Elemento Symbols | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- Symbols element (VSCT XML schema)
- VSCT XML schema elements, Symbols
ms.assetid: 1cda43d8-42a5-4b1b-a3c8-cf0401c3202f
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c8d28d225bd3a8d5c105bf54b9c63574002aed15
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160459"
---
# <a name="symbols-element"></a>Symbols (Elemento)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Define los GUID e identificadores que usan otros elementos VSCT. En el caso de código no administrado, esta información procede normalmente de los archivos de encabezado especificados por el [elemento extern](../extensibility/extern-element.md). El código administrado utiliza los elementos secundarios del elemento Symbols para definir esta información.  
  
 Si crea un archivo. Vsct a partir de un archivo. CTO existente, los símbolos se generarán como elementos secundarios del elemento Symbols. Para obtener más información, consulte [Cómo: crear un. Archivo Vsct de un existente. Archivo CTO](../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file.md).  
  
 El elemento Symbols no se debe confundir con el [elemento define](../extensibility/define-element.md), que define los pares de nombre y valor para que los utilice el preprocesador.  
  
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
|None||  
  
### <a name="child-elements"></a>Elementos secundarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|GuidSymbol|Define un símbolo GUID. GuidSymbol tiene dos atributos necesarios: nombre y valor. El nombre es el nombre del símbolo y el valor es el valor del GUID como una cadena.<br /><br /> Por ejemplo:\<GuidSymbol name="guidVsPackage1Pkg"   value="{c5f54698-101a-4846-84d3-dc748f9cd848}" />|  
|IDSymbol|Define un símbolo. IDSymbol tiene dos atributos necesarios: nombre y valor. El nombre es el nombre del símbolo y el valor es el valor del símbolo como una cadena.<br /><br /> Por ejemplo:\<IDSymbol name="MyMenuGroup" value="0x1020" />|  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[CommandTable (Elemento)](../extensibility/commandtable-element.md)|El elemento raíz del archivo. Vsct.|  
  
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
  
## <a name="see-also"></a>Consulte también  
 [Archivos de tabla de comandos de Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
