---
title: Elemento de botón ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Buttons element (VSCT XML schema)
- VSCT XML schema elements, Buttons
ms.assetid: 96dccf51-2b00-4700-9d28-924b34c21ecd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 05bd73764e96a27a92d741f144c222acc48fa518
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739931"
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
|id|Necesario. ID del identificador de comando GUID/ID.|
|priority|Opcional. Valor numérico que especifica la prioridad.|
|type|Opcional. Un valor enumerado que especifica el tipo de botón.<br /><br /> Si no se da, utiliza Button.<br /><br /> Botón<br /> Un comando estándar que aparece en las barras de herramientas (normalmente como un botón icónico), menús y menús contextuales.<br /><br /> MenuButton<br /> Elemento de menú que no ejecuta un comando, pero genera otro menú.<br /><br /> SplitDropDown<br /> Controles, como los botones Deshacer y Rehacer de la barra de herramientas estándar de Microsoft Word.|
|Condición|Opcional. Consulte [Atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento primario](../extensibility/parent-element.md)|Opcional. El elemento primario del botón.|
|[Elemento Icono](../extensibility/icon-element.md)|Opcional. El icono asociado con el botón.|
|[Elemento de indicador de comando](../extensibility/command-flag-element.md)|Necesario. Los valores CommandFlag válidos para un Button son los siguientes.<br /><br /> - AllowParams<br /><br /> - CommandWellOnly<br /><br /> - DefaultDisabled<br /><br /> - PredeterminadoInvisible<br /><br /> - DontCache<br /><br /> - DynamicItemStart<br /><br /> - DinámicaVisibilidad<br /><br /> - FixMenuController<br /><br /> - IconAndText<br /><br /> - NoButtonCustomize<br /><br /> - NoPersonalizar<br /><br /> - NoKeyCustomize<br /><br /> - NoShowOnMenuController<br /><br /> - Picto<br /><br /> - PostExec<br /><br /> - ProfferedCmd<br /><br /> - RoutetoDocs<br /><br /> - TextCascadeUseBtn<br /><br /> - TextMenuUseButton<br /><br /> - TextChanges<br /><br /> - TextChangesButton<br /><br /> - TextContextUseButton<br /><br /> - TextMenuCtrlUseMenu<br /><br /> - TextMenuUseButton<br /><br /> - TextOnly|
|[Elemento Strings](../extensibility/strings-element.md)|Necesario. El elemento secundario [ButtonText](../extensibility/buttontext-element.md) debe definirse.|
|Anotación|Comentario opcional.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento Buttons](../extensibility/buttons-element.md)|Elementos De botón de grupos.|

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se define un botón en un archivo *.vsct.*

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

## <a name="see-also"></a>Vea también
- [Archivos de tabla de comandos de Visual Studio (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
