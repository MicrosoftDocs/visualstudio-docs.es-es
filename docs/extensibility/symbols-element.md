---
title: Elemento de símbolos (Símbolos) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Symbols element (VSCT XML schema)
- VSCT XML schema elements, Symbols
ms.assetid: 1cda43d8-42a5-4b1b-a3c8-cf0401c3202f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5c24c3f84df23a07b6b16272b66b29e32ad7b911
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699346"
---
# <a name="symbols-element"></a>Symbols (Elemento)
Define GUID e iD que utilizan otros elementos VSCT. Para el código no administrado, esta información normalmente procede de los archivos de encabezado especificados por [Extern Element](../extensibility/extern-element.md). El código administrado utiliza los elementos secundarios del elemento Symbols para definir esta información.

 Si crea un archivo .vsct a partir de un archivo .cto existente, los símbolos se generarán como elementos secundarios del elemento Symbols. Para obtener más información, consulte [Cómo: crear un archivo . Archivo Vsct de un archivo . Cto Archivo](../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file).

 El elemento Symbols no debe confundirse con el [elemento Define ,](../extensibility/define-element.md)que define los pares nombre-valor para su uso por el preprocesador.

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
|GuidSymbol|Define un símbolo GUID. GuidSymbol tiene dos atributos necesarios: nombre y valor. El nombre es el nombre del símbolo y el valor es el valor del GUID como una cadena.<br /><br /> Por ejemplo:\<GuidSymbol name-"guidVsPackage1Pkg" value-"-c5f54698-101a-4846-84d3-dc748f9cd848-" />|
|IDSymbol|Define un símbolo. IDSymbol tiene dos atributos necesarios: nombre y valor. El nombre es el nombre del símbolo y el valor es el valor del símbolo como una cadena.<br /><br /> Por ejemplo:\<IDSymbol name -"MyMenuGroup" value-"0x1020" />|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[CommandTable (Elemento)](../extensibility/commandtable-element.md)|El elemento raíz del archivo .vsct.|

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
