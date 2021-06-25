---
title: Elemento CommandPlacements | Microsoft Docs
description: El elemento CommandPlacements agrupa elementos CommandPlacement y otras agrupaciones CommandPlacements. El elemento CommandPlacements es opcional.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CommandPlacements
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 78a5724a-3b9f-4c78-9c0d-8faa3924f81c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 21e0feb3913b148b4320e69461bc5035655a392d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901895"
---
# <a name="commandplacements-element"></a>Elemento CommandPlacements
El elemento CommandPlacements agrupa elementos CommandPlacement y otras agrupaciones CommandPlacements.

 El elemento CommandPlacements es opcional. Si no se deben incluir comandos, grupos o menús en una ubicación secundaria, no es necesario incluir esta sección en el *archivo .vsct.*

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
|Condición|Opcional. Vea [Atributos condicionales.](../extensibility/vsct-xml-schema-conditional-attributes.md)|

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|CommandPlacements|Agrupa elementos CommandPlacement y otras agrupaciones CommandPlacements.|
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
- [Visual Studio de tabla de comandos (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
