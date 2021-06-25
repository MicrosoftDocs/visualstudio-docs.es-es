---
title: Elemento ButtonText | Microsoft Docs
description: El elemento ButtonText permite especificar el texto que aparece en varios menús. El elemento ButtonText no puede estar en blanco aunque se especifiquen otros campos de texto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- ButtonText element (VSCT XML schema)
- VSCT XML schema elements, ButtonText
ms.assetid: 56aba884-0356-4894-ae4e-32d3938f6865
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cf20a6876dd7ba52413a11f30a3d0130b32e535d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900724"
---
# <a name="buttontext-element"></a>Elemento ButtonText
Este campo permite especificar el texto que aparece en varios menús. De forma predeterminada, el `ButtonText` elemento aparece en los controladores de menú. El `ButtonText` elemento también se convierte en el valor predeterminado si los demás campos de texto están en blanco. El `ButtonText` elemento no puede estar en blanco aunque se especifiquen los demás campos de texto.

## <a name="syntax"></a>Sintaxis

```xml
<ButtonText>My Command</ButtonText>
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos
 Ninguno.

### <a name="child-elements"></a>Elementos secundarios
 Ninguno.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento Strings](../extensibility/strings-element.md)|Agrupa elementos de texto, como `ButtonText` y `CommandName` .|

## <a name="text-value"></a>Valor de texto
 El valor de texto del elemento proporciona el texto que se muestra para los elementos de menú, los combinados y otros elementos de la interfaz de usuario `ButtonText` (UI) que tienen texto visible.

## <a name="see-also"></a>Consulta también
- [Visual Studio de tabla de comandos (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
