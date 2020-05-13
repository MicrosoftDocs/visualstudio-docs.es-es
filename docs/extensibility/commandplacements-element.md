---
title: Elemento CommandPlacements (CommandPlacements Element) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- CommandPlacements
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 78a5724a-3b9f-4c78-9c0d-8faa3924f81c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a72b087652a654b563fd4e00bacc52290a29fe1c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739700"
---
# <a name="commandplacements-element"></a>Elemento CommandPlacements
El elemento CommandPlacements agrupa elementos CommandPlacement y otras agrupaciones CommandPlacements.

 El elemento CommandPlacements es opcional. Si no se deben incluir comandos, grupos o menús en una ubicación secundaria, no es necesario incluir esta sección en el archivo *.vsct.*

## <a name="syntax"></a>Sintaxis

```xml
<CommandPlacements>
  <CommandPlacement>... </CommandPlacement>
  <CommandPlacement>... </CommandPlacement>
</CommandPlacements>
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos

|Atributo|Descripción|
|---------------|-----------------|
|Condición|Opcional. Consulte [Atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|CommandPlacements|Agrupa commandPlacement elementos y otras agrupaciones CommandPlacements.|
|[Elemento CommandPlacement](../extensibility/commandplacement-element.md)|Permite incluir botones, grupos y menús en más de un grupo o menú.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Define todos los elementos que representan comandos.|

## <a name="example"></a>Ejemplo

```xml
<CommandPlacements>
  <CommandPlacement guid="guidWidgetPackage" id="cmdidInsertOptions"
    priority="0x0300">
    <Parent guid="cmdGuidWidgetCommands" id="menuIDEditWidget"/>
  </CommandPlacement>
</CommandPlacements>
```

## <a name="see-also"></a>Consulte también
- [Elemento CommandPlacement](../extensibility/commandplacement-element.md)
- [Archivos de tabla de comandos de Visual Studio (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
