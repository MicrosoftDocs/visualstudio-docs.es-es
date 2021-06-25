---
title: Elemento Symbols | Microsoft Docs
description: El elemento Symbols define LOS GUID y los ID que usan otros elementos VSCT. Este artículo contiene un ejemplo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Symbols element (VSCT XML schema)
- VSCT XML schema elements, Symbols
ms.assetid: 1cda43d8-42a5-4b1b-a3c8-cf0401c3202f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b593f353714f2fbb6f5b726fa2bbc0da449043ea
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901739"
---
# <a name="symbols-element"></a>Symbols (Elemento)
Define los GUID y los ID que usan otros elementos VSCT. En el caso del código no administrado, esta información procede normalmente de los archivos de encabezado especificados por [el elemento Extern](../extensibility/extern-element.md). El código administrado usa los elementos secundarios del elemento Symbols para definir esta información.

 Si crea un archivo .vsct a partir de un archivo .cto existente, los símbolos se generarán como elementos secundarios del elemento Symbols. Para obtener más información, [vea Cómo: Crear un . Archivo Vsct de un objeto existente. Archivo Cto](../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file).

 El elemento Symbols no debe confundirse con [el elemento Define ,](../extensibility/define-element.md)que define pares nombre-valor para su uso por parte del preprocesador.

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
|Ninguno||

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|GuidSymbol|Define un símbolo GUID. GuidSymbol tiene dos atributos obligatorios: nombre y valor. El nombre es el nombre del símbolo y el valor es el valor del GUID como una cadena.<br /><br /> Por ejemplo:\<GuidSymbol name="guidVsPackage1Pkg"   value="{c5f54698-101a-4846-84d3-dc748f9cd848}" />|
|IDSymbol|Define un símbolo. IDSymbol tiene dos atributos obligatorios: nombre y valor. El nombre es el nombre del símbolo y el valor es el valor del símbolo como una cadena.<br /><br /> Por ejemplo:\<IDSymbol name="MyMenuGroup" value="0x1020" />|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[CommandTable (Elemento)](../extensibility/commandtable-element.md)|Elemento raíz del archivo .vsct.|

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
- [Archivos de tabla de comandos de Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
