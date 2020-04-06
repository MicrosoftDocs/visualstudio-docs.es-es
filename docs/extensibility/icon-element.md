---
title: Elemento de icono (Icon Element) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Icon
- Icon element (VSCT XML schema)
ms.assetid: 73c58fe3-d53c-4f4e-b025-29567c6cbb7c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cf4f8a69e565620007fba4b9970ce96bb1513995
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710517"
---
# <a name="icon-element"></a>Elemento Icono
El atributo guid de la etiqueta Icon es el guid de un mapa de bits definido. El `id` atributo selecciona la ranura en la franja de mapa de bits. Este elemento es opcional. Si no se incluye este elemento, se implicará el valor de **guidOfficeIcon:msotcidNoIcon.**

## <a name="syntax"></a>Sintaxis

```xml
<Icon guid="guidImages" id="bmpPic1" />
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos

|Atributo|Descripción|
|---------------|-----------------|
|guid|Necesario. El guid de un mapa de bits definido.|
|id|Necesario. Selecciona la ranura en la franja de mapa de bits.|

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|Ninguno.|Ninguno.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento Buttons](../extensibility/buttons-element.md)||

## <a name="see-also"></a>Vea también
- [Archivos de tabla de comandos de Visual Studio (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
