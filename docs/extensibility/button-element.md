---
title: Elemento Button | Microsoft Docs
description: 'El elemento de botón define un elemento con el que el usuario puede interactuar. Los botones pueden ser tipos diferentes: Button, MenuButton y SplitDropDown.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Buttons element (VSCT XML schema)
- VSCT XML schema elements, Buttons
ms.assetid: 96dccf51-2b00-4700-9d28-924b34c21ecd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ec0640313195d6a15599d1a765081557c0c1a75a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105068152"
---
# <a name="button-element"></a>Elemento Button
Define un elemento con el que el usuario puede interactuar. Los botones pueden ser de diferentes tipos: Button, MenuButton y SplitDropDown.

## <a name="syntax"></a>Sintaxis

```
<Button guid="guidMyCommandSet" id="MyCommand" priority="0x102" type="button">
  <Parent>... </Parent>
  <Icon>... </Icon>
  <CommandFlag>... </CommandFlag>
  <Strings>... </Strings>
</Button>
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos

|Atributo|Descripción|
|---------------|-----------------|
|guid|Necesario. GUID del identificador del comando GUID/ID.|
|id|Necesario. IDENTIFICADOR del identificador del comando GUID/ID.|
|priority|Opcional. Valor numérico que especifica la prioridad.|
|type|Opcional. Valor enumerado que especifica el tipo de botón.<br /><br /> Si no se especifica, usa el botón.<br /><br /> Botón<br /> Comando estándar que aparece en las barras de herramientas (normalmente como un botón de iconos), menús y menús contextuales.<br /><br /> MenuButton<br /> Un elemento de menú que no ejecuta un comando, pero genera otro menú.<br /><br /> SplitDropDown<br /> Controles, como los botones deshacer y rehacer de la barra de herramientas estándar de Microsoft Word.|
|Condición|Opcional. Vea [atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento primario](../extensibility/parent-element.md)|Opcional. Elemento primario del botón.|
|[Elemento Icon](../extensibility/icon-element.md)|Opcional. Icono asociado al botón.|
|[Elemento de marca de comando](../extensibility/command-flag-element.md)|Necesario. Los valores válidos de CommandFlag para un botón son los siguientes.<br /><br /> - AllowParams<br /><br /> - CommandWellOnly<br /><br /> - DefaultDisabled<br /><br /> - DefaultInvisible<br /><br /> - DontCache<br /><br /> - DynamicItemStart<br /><br /> - DynamicVisibility<br /><br /> - FixMenuController<br /><br /> - IconAndText<br /><br /> - NoButtonCustomize<br /><br /> -Nocustomizate<br /><br /> - NoKeyCustomize<br /><br /> - NoShowOnMenuController<br /><br /> -PICT<br /><br /> -Postexec<br /><br /> - ProfferedCmd<br /><br /> - RouteToDocs<br /><br /> - TextCascadeUseBtn<br /><br /> - TextMenuUseButton<br /><br /> -Textchanges al<br /><br /> - TextChangesButton<br /><br /> - TextContextUseButton<br /><br /> - TextMenuCtrlUseMenu<br /><br /> - TextMenuUseButton<br /><br /> -TextOnly|
|[Elemento Strings](../extensibility/strings-element.md)|Necesario. Se debe definir el [elemento ButtonText](../extensibility/buttontext-element.md) secundario.|
|Anotación|Comentario opcional.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Buttons, elemento](../extensibility/buttons-element.md)|Agrupa los elementos de botón.|

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se define un botón en un archivo *. Vsct* .

 ```xml
<Button guid="guidMenuTextCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
    <Parent guid="guidMenuTextCmdSet" id="MyMenuGroup" />
    <Icon guid="guidImages" id="bmpPic1" />
    <CommandFlag>TextChanges</CommandFlag>
    <Strings>
          <CommandName>cmdidMyCommand</CommandName>
          <ButtonText>My Command name</ButtonText>
    </Strings>
</Button>
 ```

## <a name="see-also"></a>Consulte también
- [Archivos de tabla de comandos de Visual Studio (. Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
