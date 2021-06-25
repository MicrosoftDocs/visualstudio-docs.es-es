---
title: Elemento primario | Microsoft Docs
description: El elemento Parent especifica que un elemento es un elemento primario de un botón, cuadro combinado, menú o grupo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Parent
- Parent element (VSCT XML schema)
ms.assetid: e4624ac8-1b9a-4940-910a-528a661cefad
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3dbf7202ac7fb94762ea132a2620625fae97ddfb
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901557"
---
# <a name="parent-element"></a>Elemento primario
El elemento primario de un botón o cuadro combinado solo puede ser un grupo. El elemento primario de un menú o grupo puede ser cualquier otro menú o grupo. En un [elemento CommandPlacement](../extensibility/commandplacement-element.md), este elemento es obligatorio; en todas las demás instancias es opcional. Si se omite este elemento, se implicará el elemento `Group_Undefined:0` primario de .

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
|id|Necesario. Identificador del identificador de comando GUID/ID.|

### <a name="child-elements"></a>Elementos secundarios
 Ninguno

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Define todos los elementos que representan comandos que un VSPackage proporciona al entorno de desarrollo integrado (IDE). Por ejemplo, elementos de menú, menús, barras de herramientas y cuadros combinados.|
|[Elemento Buttons](../extensibility/buttons-element.md)|Elementos [del elemento Groups Button.](../extensibility/button-element.md)|
|[Elemento Menus](../extensibility/menus-element.md)|Define todos los menús que implementa un VSPackage.|
|[Elemento Groups](../extensibility/groups-element.md)|Contiene entradas que definen los grupos de comandos de un VSPackage.|

## <a name="see-also"></a>Consulta también
- [Visual Studio archivos de tabla de comandos (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
