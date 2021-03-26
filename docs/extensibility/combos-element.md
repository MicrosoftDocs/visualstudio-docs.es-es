---
title: Comboboxs (elemento) | Microsoft Docs
description: El elemento combinados agrupa los elementos combinados, que definen los comandos que aparecen en un cuadro combinado. Este artículo contiene un ejemplo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Combos element (VSCT XML schema)
- VSCT XML schema elements, Combos
ms.assetid: ef48d2d2-0c47-4f93-8cfe-52026b6c463e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: be9135e2f863f3ab277e6c7408579d7ef8242bce
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089724"
---
# <a name="combos-element"></a>Comboboxs (elemento)
Agrupa los elementos de [elemento combinado](../extensibility/combo-element.md) .

## <a name="syntax"></a>Sintaxis

```
<Combos>
  <Combo>... </Combo>
  <Combo>... </Combo>
</Combos>
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos

|Atributo|Descripción|
|---------------|-----------------|
|Condición|Opcional. Vea [atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Comboboxs (elemento)](../extensibility/combos-element.md)|Agrupa los elementos combinados.|
|[Elemento combinado](../extensibility/combo-element.md)|Define los comandos que aparecen en un cuadro combinado.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento Commands](../extensibility/commands-element.md)|Representa la colección de comandos de la barra de herramientas de VSPackage.|

## <a name="example"></a>Ejemplo

```
<Combos>
  <Combo guid="guidWidgetPackage" id="cmdidInsertOptions"
    defaultWidth="100" idCommandList="cmdidGetInsertOptionsList">
    <CommandFlag>DynamicVisibility</CommandFlag>
    <Strings>
      <ButtonText>Select Insert Options</ButtonText>
    </Strings>
  </Combo>

  <Combo guid="guidWidgetPackage" id="cmdidInsertOptions"
    priority="0x0500" type="DropDownCombo" defaultWidth="100"
    idCommandList="cmdidGetInsertOptionsList">
    <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit">
    <CommandFlag>DynamicVisibility</CommandFlag>
    <Strings>
      <ButtonText>Select Insert Options</ButtonText>
    </Strings>
  </Combo>
</Combos>
```

## <a name="see-also"></a>Consulte también
- [Cómo agrega VSPackages los elementos de la interfaz de usuario](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Comandos, menús y barras de herramientas](../extensibility/internals/commands-menus-and-toolbars.md)
