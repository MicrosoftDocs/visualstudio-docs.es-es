---
title: Elemento Icon | Microsoft Docs
description: Obtenga información sobre el elemento Icon, que representa los iconos que se usan en las extensiones del IDE de Visual Studio, que incluye los atributos para el mapa de bits usado y la ranura en la franja de mapa de bits.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Icon
- Icon element (VSCT XML schema)
ms.assetid: 73c58fe3-d53c-4f4e-b025-29567c6cbb7c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 52ccb8093b61e0458f7c3caefea6f826609aa51d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105082145"
---
# <a name="icon-element"></a>Elemento Icon
El atributo GUID de la etiqueta de icono es el GUID de un mapa de bits definido. El `id` atributo selecciona la ranura en la franja de mapa de bits. Este elemento es opcional. Si este elemento no se incluye el valor de **guidOfficeIcon: msotcidNoIcon** será implícito.

## <a name="syntax"></a>Sintaxis

```xml
<Icon guid="guidImages" id="bmpPic1" />
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos

|Atributo|Descripción|
|---------------|-----------------|
|guid|Necesario. GUID de un mapa de bits definido.|
|id|Necesario. Selecciona la ranura en la franja de mapa de bits.|

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|Ninguno.|Ninguno.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Buttons, elemento](../extensibility/buttons-element.md)||

## <a name="see-also"></a>Consulte también
- [Archivos de tabla de comandos de Visual Studio (. Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
