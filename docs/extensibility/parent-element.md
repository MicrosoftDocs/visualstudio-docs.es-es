---
title: Elemento principal ( Parent Element) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Parent
- Parent element (VSCT XML schema)
ms.assetid: e4624ac8-1b9a-4940-910a-528a661cefad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8c018505ba06762bf8426f266b24ee1835313c29
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702225"
---
# <a name="parent-element"></a>Elemento primario
El elemento primario de un botón o cuadro combinado solo puede ser un grupo. El elemento primario de un menú o grupo puede ser cualquier otro menú o grupo. En un [elemento CommandPlacement](../extensibility/commandplacement-element.md), este elemento es necesario; en todos los demás casos es opcional. Si se omite este elemento, `Group_Undefined:0` se implicará el elemento primario de.

## <a name="syntax"></a>Sintaxis

```xml
<Parent guid="guidMyCommandSet" id="MyParentGroupOrMenu" />
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos

|Atributo|Descripción|
|---------------|-----------------|
|guid|Necesario. GUID del identificador de comando GUID/ID.|
|id|Necesario. ID del identificador de comando GUID/ID.|

### <a name="child-elements"></a>Elementos secundarios
 None

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Define todos los elementos que representan comandos que un VSPackage proporciona al entorno de desarrollo integrado (IDE). Por ejemplo, elementos de menú, menús, barras de herramientas y cuadros combinados.|
|[Elemento Buttons](../extensibility/buttons-element.md)|Elementos de [elemento Button](../extensibility/button-element.md) de grupos.|
|[Elemento Menús](../extensibility/menus-element.md)|Define todos los menús que implementa un VSPackage.|
|[Elemento Grupos](../extensibility/groups-element.md)|Contiene entradas que definen los grupos de comandos de un VSPackage.|

## <a name="see-also"></a>Vea también
- [Archivos de tabla de comandos de Visual Studio (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
