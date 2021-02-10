---
title: Opciones, editor de texto, XML y formato
description: Obtenga información sobre cómo usar la página Formato de la sección XML para especificar cómo se aplica formato a los elementos y atributos en los documentos XML.
ms.custom: SEO-VS-2020
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Formatting
ms.assetid: 203e60b2-7b80-4ff4-9fa1-aa9f4374377b
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: b5e3674c955b229c4c517db5d1dab3d36830da5d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99932324"
---
# <a name="options-text-editor-xml-formatting"></a>Opciones, editor de texto, XML y formato

Use la página de opciones **Formato** para especificar cómo se aplica formato a los elementos y atributos en los documentos XML. Para acceder a opciones de formato de XML, elija **Herramientas** > **Opciones** > **Editor de texto** > **XML** y, a continuación, elija **Formato**.

## <a name="attributes"></a>Atributos

**Preservar el formato manual de atributos**

No vuelve a dar formato a los atributos. Esta es la configuración predeterminada.

> [!NOTE]
> Si los atributos se encuentran en varias líneas, el editor sangra cada línea de atributos para que coincida con el sangrado del elemento primario.

**Alinear los atributos en líneas separadas**

Los atributos segundo y siguientes se alinean verticalmente para coincidir con el sangrado del primer atributo. La siguiente prueba XML es un ejemplo de cómo se alinearían los atributos:

```xml
<item id = "123-A"
      name = "hammer"
      price = "9.95">
</item>
```

## <a name="auto-reformat"></a>Formatear automáticamente

**Al pegar del Portapapeles**

Vuelve a dar formato al texto XML pegado desde el portapapeles.

**Al terminar la etiqueta final**

Vuelve a dar formato al elemento cuando se completa la etiqueta final.

## <a name="mixed-content"></a>Contenido mixto

**Formatear contenido mixto de forma predeterminada**

Intenta volver a dar formato al contenido mixto, excepto si se encuentra en un ámbito `xml:space="preserve"`. Esta es la configuración predeterminada.

Si un elemento contiene una mezcla de texto y marcado, el contenido se considera mixto. A continuación se incluye un ejemplo de un elemento con contenido mixto.

```xml
<dir>c:\data\AlphaProject\
  <file readOnly="false">test1.txt</file>
  <file readOnly="false">test2.txt</file>
</dir>
```

## <a name="see-also"></a>Consulte también

- [Opciones XML: otras opciones](options-text-editor-xml-miscellaneous.md)
- [Herramientas XML en Visual Studio](../../xml-tools/xml-tools-in-visual-studio.md)
