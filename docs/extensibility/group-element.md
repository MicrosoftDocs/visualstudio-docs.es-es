---
title: Group (elemento) | Microsoft Docs
description: El elemento Group define un grupo de comandos VSPackage. En este artículo se describen los atributos, los elementos secundarios y los elementos primarios.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Groups
- Groups element (VSCT XML schema)
ms.assetid: 69faee18-cbf4-470a-b952-c1919c583df8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d0d39d4e4f795ddecab21765db43ba1a2f629dd7
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2020
ms.locfileid: "96993859"
---
# <a name="group-element"></a>Group, elemento
Define un grupo de comandos de VSPackage.

## <a name="syntax"></a>Sintaxis

```xml
<Group guid="guidMyCommandSet" id="MyGroup" priority="0x101">
  <Parent>... </Parent>
</Group>
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos

|Atributo|Descripción|
|---------------|-----------------|
|guid|Obligatorio. GUID del identificador del comando GUID/ID.|
|id|Obligatorio. IDENTIFICADOR del identificador del comando GUID/ID.|
|priority|Opcional. Valor numérico que especifica la prioridad.|
|Condición|Opcional. Vea [atributos condicionales](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|Parent|Opcional. Elemento primario del botón.|
|Anotación|Comentario opcional.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento Groups](../extensibility/groups-element.md)|Contiene entradas que definen los grupos de comandos de un VSPackage.|

## <a name="example"></a>Ejemplo

```xml
<Group guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit">
  <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_MAINMENU"/>
</Group>
```

## <a name="see-also"></a>Consulte también
- [Archivos de tabla de comandos de Visual Studio (. Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
