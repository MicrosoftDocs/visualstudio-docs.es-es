---
title: Elemento ButtonText (Elemento ButtonText) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ButtonText element (VSCT XML schema)
- VSCT XML schema elements, ButtonText
ms.assetid: 56aba884-0356-4894-ae4e-32d3938f6865
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 59308feea2002a18662a7c04b95a92a920f934c4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739909"
---
# <a name="buttontext-element"></a>Elemento ButtonText
Este campo le permite especificar el texto que aparece en varios menús. De forma `ButtonText` predeterminada, el elemento aparece en los controladores de menú. El `ButtonText` elemento también se convierte en el valor predeterminado si los demás campos de texto están en blanco. El `ButtonText` elemento no puede estar en blanco aunque se especifiquen los demás campos de texto.

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
|[Elemento Strings](../extensibility/strings-element.md)|Agrupa elementos de `ButtonText` `CommandName`texto, como y .|

## <a name="text-value"></a>Valor de texto
 El valor de `ButtonText` texto del elemento proporciona el texto que se muestra para los elementos de menú, combos y otros elementos de interfaz de usuario (UI) que tienen texto visible.

## <a name="see-also"></a>Vea también
- [Archivos de tabla de comandos de Visual Studio (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
