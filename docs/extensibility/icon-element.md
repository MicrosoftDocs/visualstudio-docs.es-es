---
title: Icono de elemento | Microsoft Docs
description: Obtenga información sobre el elemento Icon, que representa los iconos usados en las extensiones del IDE de Visual Studio, que incluye atributos para el mapa de bits utilizado y la ranura en la franja de mapa de bits.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Icon
- Icon element (VSCT XML schema)
ms.assetid: 73c58fe3-d53c-4f4e-b025-29567c6cbb7c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7ad5bfdf000232ef92a9e9a27b12152df36a4335
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900829"
---
# <a name="icon-element"></a>Elemento Icon
El atributo GUID de la etiqueta Icon es el GUID de un mapa de bits definido. El `id` atributo selecciona la ranura en la franja de mapa de bits. Este elemento es opcional. Si este elemento no se incluye, el valor **de guidOfficeIcon:msotcidNoIcon** estará implícito.

## <a name="syntax"></a>Sintaxis

```xml
<Icon guid="guidImages" id="bmpPic1" />
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos

|Atributo|Descripción|
|---------------|-----------------|
|guid|Necesario. Guid de un mapa de bits definido.|
|id|Necesario. Selecciona la ranura de la franja de mapa de bits.|

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|Ninguno.|Ninguno.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento Buttons](../extensibility/buttons-element.md)||

## <a name="see-also"></a>Consulta también
- [Visual Studio de tabla de comandos (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
