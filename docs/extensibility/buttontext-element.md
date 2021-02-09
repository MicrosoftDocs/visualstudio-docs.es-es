---
title: ButtonText, elemento | Microsoft Docs
description: El elemento ButtonText le permite especificar el texto que aparece en varios menús. El elemento ButtonText no puede estar en blanco aunque se hayan especificado otros campos de texto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ButtonText element (VSCT XML schema)
- VSCT XML schema elements, ButtonText
ms.assetid: 56aba884-0356-4894-ae4e-32d3938f6865
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b03b5fce58795488f6c379fcf93e5f7fea074e13
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927176"
---
# <a name="buttontext-element"></a>Elemento ButtonText
Este campo le permite especificar el texto que aparece en varios menús. De forma predeterminada, el `ButtonText` elemento aparece en los controladores de menús. El `ButtonText` elemento también se convierte en el valor predeterminado si los demás campos de texto están en blanco. El `ButtonText` elemento no puede estar en blanco ni siquiera si se especifican los demás campos de texto.

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
|[Elemento Strings](../extensibility/strings-element.md)|Agrupa los elementos de texto, como `ButtonText` y `CommandName` .|

## <a name="text-value"></a>Valor de texto
 El valor de texto del `ButtonText` elemento proporciona el texto que se muestra para los elementos de menú, los cuadros combinados y otros elementos de la interfaz de usuario que tienen texto visible.

## <a name="see-also"></a>Vea también
- [Archivos de tabla de comandos de Visual Studio (. Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
