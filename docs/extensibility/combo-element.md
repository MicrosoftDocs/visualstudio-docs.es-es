---
title: Elemento combinado ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Combos element (VSCT XML schema)
- VSCT XML schema elements, Combos
ms.assetid: 392e3063-f0a0-4130-9583-23bd2aa3fa36
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 18ff9d9e20ec221a86f1cce5f9c43a4e47ed6dc2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739822"
---
# <a name="combo-element"></a>Elemento combinado
Define los comandos que aparecen en un cuadro combinado. Hay cuatro tipos de cuadros combinados, como se indica a continuación: DropDownCombo, DynamicCombo, IndexCombo y MRUCombo.

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
|id|Necesario. ID del identificador de comando GUID/ID.|
|defaultWidth|Necesario. Entero que especifica un ancho de píxel para el cuadro combinado.|
|idCommandList|Necesario. Un identificador que se envía al destino del comando activo para recuperar la lista de elementos que se mostrarán en el cuadro combinado. El identificador estará en el mismo ámbito GUID que el control.|
|priority|Opcional. Valor numérico que especifica la prioridad.|
|type|Opcional. Un valor enumerado que especifica el tipo de botón.<br /><br /> Si no se da, utiliza Button.<br /><br /> DropDownCombo<br /> El VSPackage es responsable de rellenar el contenido de este cuadro combinado. El usuario no puede escribir nada en el cuadro de texto de esta lista desplegable.<br /><br /> DynamicCombo<br /> El VSPackage es responsable de rellenar el contenido de este cuadro combinado. El usuario puede editar este combo y también seleccionar elementos en él.<br /><br /> IndexCombo<br /> Lo mismo que DynamicCombo excepto que genera el índice del elemento en lugar de su texto.<br /><br /> MRUCombo<br /> Lleno por el entorno de desarrollo integrado (IDE) en nombre del VSPackage.  El usuario puede editar en este cuadro combinado. El IDE recuerda hasta las últimas 16 entradas por cuadro combinado.<br /><br /> Cuando el usuario selecciona algo en el cuadro combinado o escribe algo nuevo, el IDE notifica el VSPackage adecuado.|
|Condición|Opcional. Consulte [Atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|Parent|Opcional. El elemento primario del botón.|
|CommandFlag|Necesario. Consulte [Elemento de indicador de comando](../extensibility/command-flag-element.md). Los valores CommandFlag válidos para un Button son los siguientes.<br /><br /> - CaseSensitive<br /><br /> - CommandWellOnly<br /><br /> - DefaultDisabled<br /><br /> - PredeterminadoInvisible<br /><br /> - DinámicaVisibilidad<br /><br /> - FilterKeys<br /><br /> - IconAndText<br /><br /> - NoAutoComplete<br /><br /> - NoButtonCustomize<br /><br /> - NoPersonalizar<br /><br /> - NoKeyCustomize<br /><br /> - StretchHorizontally|
|Cadenas|Necesario. Consulte [Elemento Cadenas](../extensibility/strings-element.md). El elemento secundario ButtonText debe definirse.|
|Anotación|Comentario opcional.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento Comandos](../extensibility/commands-element.md)|Representa la colección de comandos de la barra de herramientas de VSPackage.|

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
- [Archivos de tabla de comandos de Visual Studio (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
