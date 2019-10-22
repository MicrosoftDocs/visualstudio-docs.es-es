---
title: Formato, XML, editor de texto, opciones (cuadro de diálogo) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: bb539b3a-027c-4b2f-906e-403e0e22ba8d
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 962321a1ab1a1ca5332300eea0d21781a9e4bbf5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670972"
---
# <a name="formatting-xml-text-editor-options-dialog-box"></a>Formato, XML, Editor de texto, Cuadro de diálogo Opciones
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este cuadro de diálogo permite especificar las opciones de formato del Editor XML. Puede tener acceso al cuadro de diálogo **Opciones** desde el menú **herramientas** .

> [!NOTE]
> Estas opciones están disponibles cuando se selecciona la carpeta **Editor de texto** , la carpeta **XML** y, a continuación, la opción **formato** del cuadro de diálogo **Opciones** .

## <a name="attributes"></a>Atributos
 **Conservar el formato manual de atributos** No se cambia el formato de los atributos. Este es el valor predeterminado.

> [!NOTE]
> Si los atributos están en varias líneas, el editor aplica sangría a cada línea de atributos para que coincida con la sangría del elemento primario.

 **Alinear los atributos en su propia línea** Alinea verticalmente el segundo y los atributos subsiguientes para que coincidan con la sangría del primer atributo. La siguiente prueba XML es un ejemplo de cómo se alinearían los atributos.

```
<item id = "123-A"
      name = "hammer"
      price = "9.95">
</item>
```

## <a name="auto-reformat"></a>Formatear automáticamente
 **Al pegar desde el portapapeles** Cambiar el formato del texto XML pegado desde el portapapeles.

 **Al finalizar la etiqueta de cierre** Vuelva a dar formato al elemento cuando se complete la etiqueta de cierre.

## <a name="mixed-content"></a>Contenido mixto
 **Conservar el contenido mixto de forma predeterminada** Determina si el editor reformatea el contenido mixto. De forma predeterminada, el editor intenta volver a dar formato al contenido mixto, excepto cuando el contenido se halla en un ámbito `xml:space="preserve"`.

 Si un elemento contiene una mezcla de texto y marcado, se considera que el contenido es mixto. A continuación se muestra un ejemplo de un elemento con contenido mixto.

```
<dir>c:\data\AlphaProject\
  <file readOnly="false">test1.txt</file>
  <file readOnly="false">test2.txt</file>
</dir>
```

## <a name="see-also"></a>Vea también
 [Propiedades de documento XML, ventana Propiedades](../xml-tools/xml-document-properties-properties-window.md) [componentes del editor XML](../xml-tools/xml-editor-components.md)
