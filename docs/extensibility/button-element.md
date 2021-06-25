---
title: Elemento Button | Microsoft Docs
description: 'El elemento Button define un elemento con el que el usuario puede interactuar. Los botones pueden ser de diferentes tipos: Button, MenuButton y SplitDropDown.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Buttons element (VSCT XML schema)
- VSCT XML schema elements, Buttons
ms.assetid: 96dccf51-2b00-4700-9d28-924b34c21ecd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 630d848c40b13a929c3dd91b47e1c35529efaa50
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901752"
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
|guid|Necesario. GUID del identificador de comando GUID/ID.|
|id|Necesario. Identificador del identificador de comando GUID/ID.|
|priority|Opcional. Valor numérico que especifica la prioridad.|
|type|Opcional. Valor enumerado que especifica el tipo de botón.<br /><br /> Si no se da, usa Button.<br /><br /> Botón<br /> Un comando estándar que aparece en las barras de herramientas (normalmente como un botón icono), menús y menús contextuales.<br /><br /> MenuButton<br /> Elemento de menú que no ejecuta un comando, pero genera otro menú.<br /><br /> SplitDropDown<br /> Controles, como los botones Deshacer y Rehacer de la barra de herramientas estándar de Microsoft Word.|
|Condición|Opcional. Vea [Atributos condicionales.](../extensibility/vsct-xml-schema-conditional-attributes.md)|

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento primario](../extensibility/parent-element.md)|Opcional. Elemento primario del botón.|
|[Elemento Icon](../extensibility/icon-element.md)|Opcional. Icono asociado al botón.|
|[Elemento De marca de comando](../extensibility/command-flag-element.md)|Necesario. Los valores de CommandFlag válidos para un botón son los siguientes.<br /><br /> - AllowParams<br /><br /> - CommandWellOnly<br /><br /> - DefaultDisabled<br /><br /> - DefaultInvisible<br /><br /> - DontCache<br /><br /> - DynamicItemStart<br /><br /> - DynamicVisibility<br /><br /> - FixMenuController<br /><br /> - IconAndText<br /><br /> - NoButtonCustomize<br /><br /> - NoCustomize<br /><br /> - NoKeyCustomize<br /><br /> - NoShowOnMenuController<br /><br /> - Fuenía<br /><br /> - PostExec<br /><br /> - ProfferedCmd<br /><br /> - RouteToDocs<br /><br /> - TextCascadeUseBtn<br /><br /> - TextMenuUseButton<br /><br /> - TextChanges<br /><br /> - TextChangesButton<br /><br /> - TextContextUseButton<br /><br /> - TextMenuCtrlUseMenu<br /><br /> - TextMenuUseButton<br /><br /> - TextOnly|
|[Elemento Strings](../extensibility/strings-element.md)|Necesario. Se debe [definir el elemento ButtonText](../extensibility/buttontext-element.md) secundario.|
|Anotación|Comentario opcional.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento Buttons](../extensibility/buttons-element.md)|Elementos De botón de grupos.|

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se define un botón en un *archivo .vsct.*

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

## <a name="see-also"></a>Consulta también
- [Visual Studio de tabla de comandos (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
