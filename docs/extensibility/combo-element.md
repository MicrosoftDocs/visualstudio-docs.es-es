---
title: Combo Element | Microsoft Docs
description: 'El elemento Combo define los comandos que aparecen en un cuadro combinado. Hay cuatro tipos: DropDownCombo, DynamicCombo, IndexCombo y MRUCombo.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Combos element (VSCT XML schema)
- VSCT XML schema elements, Combos
ms.assetid: 392e3063-f0a0-4130-9583-23bd2aa3fa36
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 431d68b6e545506f5fc90cc5a98a52dd4f1c33ad
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904960"
---
# <a name="combo-element"></a>Elemento combinado
Define los comandos que aparecen en un cuadro combinado. Hay cuatro tipos de cuadros combinados, como se muestra a continuación: DropDownCombo, DynamicCombo, IndexCombo y MRUCombo.

## <a name="syntax"></a>Sintaxis

```xml
<combo guid="guidMyCommandSet" id="MyCommand" defaultWidth="20" idCommandList="MyCommandListID" priority="0x102" type="DropDownCombo">
  <Parent>... </Parent
  <CommandFlag>... </CommandFlag>
  <Strings>... </Strings>
</combo>
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos

|Atributo|Descripción|
|---------------|-----------------|
|guid|Necesario. GUID del identificador de comando GUID/ID.|
|id|Necesario. Identificador del identificador de comando GUID/ID.|
|defaultWidth|Necesario. Entero que especifica un ancho de píxel para el cuadro combinado.|
|idCommandList|Necesario. Identificador que se envía al destino del comando activo para recuperar la lista de elementos que se mostrarán en el cuadro combinado. El identificador estará en el mismo ámbito GUID que el control .|
|priority|Opcional. Valor numérico que especifica la prioridad.|
|type|Opcional. Valor enumerado que especifica el tipo de botón.<br /><br /> Si no se da, usa Button.<br /><br /> DropDownCombo<br /> VSPackage es responsable de rellenar el contenido de este cuadro combinado. El usuario no puede escribir nada en el cuadro de texto de esta lista desplegable.<br /><br /> DynamicCombo<br /> VSPackage es responsable de rellenar el contenido de este cuadro combinado. El usuario puede editar este combinado y también seleccionar elementos en él.<br /><br /> IndexCombo<br /> Igual que DynamicCombo, salvo que genera el índice del elemento en lugar de su texto.<br /><br /> MRUCombo<br /> Rellenado por el entorno de desarrollo integrado (IDE) en nombre del VSPackage.  El usuario puede editar en este cuadro combinado. El IDE recuerda hasta las últimas 16 entradas por cuadro combinado.<br /><br /> Cuando el usuario selecciona algo en el cuadro combinado o escribe algo nuevo, el IDE notifica al VSPackage adecuado.|
|Condición|Opcional. Vea [Atributos condicionales.](../extensibility/vsct-xml-schema-conditional-attributes.md)|

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|Parent|Opcional. Elemento primario del botón.|
|CommandFlag|Necesario. Vea [Elemento de marca command](../extensibility/command-flag-element.md). Los valores de CommandFlag válidos para un botón son los siguientes.<br /><br /> - Sin mayúsculas de minúsculas<br /><br /> - CommandWellOnly<br /><br /> - DefaultDisabled<br /><br /> - DefaultInvisible<br /><br /> - DynamicVisibility<br /><br /> - FilterKeys<br /><br /> - IconAndText<br /><br /> - NoAutoComplete<br /><br /> - NoButtonCustomize<br /><br /> - NoCustomize<br /><br /> - NoKeyCustomize<br /><br /> - StretchHorizontally|
|Cadenas|Necesario. Vea [Elemento Strings](../extensibility/strings-element.md). Se debe definir el elemento ButtonText secundario.|
|Anotación|Comentario opcional.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento Commands](../extensibility/commands-element.md)|Representa la colección de comandos en la barra de herramientas de VSPackage.|

## <a name="example"></a>Ejemplo

```xml
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
```

## <a name="see-also"></a>Consulte también
- [Visual Studio de tabla de comandos (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
