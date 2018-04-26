---
title: Formato, XML, Editor de texto, Cuadro de diálogo Opciones
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: reference
ms.assetid: bb539b3a-027c-4b2f-906e-403e0e22ba8d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f1046655812bf88f51af7590fd1b39ccea11f8eb
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="formatting-xml-text-editor-options-dialog-box"></a>Formato, XML, Editor de texto, Cuadro de diálogo Opciones

Este cuadro de diálogo permite especificar las opciones de formato del Editor XML. Puede tener acceso a la **opciones** cuadro de diálogo desde el **herramientas** menú.

> [!NOTE]
> Estas opciones están disponibles cuando se selecciona el **Editor de texto** carpeta, el **XML** carpeta y, a continuación, el **formato** opción desde el **opciones** cuadro de diálogo.

## <a name="attributes"></a>Atributos
 **Preservar el formato manual de atributos**

 No se vuelve a dar formato a los atributos. Este es el valor predeterminado.

> [!NOTE]
> Si los atributos están en varias líneas, el editor aplica sangría a cada línea de atributos para que coincida con la sangría del elemento primario.

 **Alinear los atributos en su propia línea**

 Alinea el segundo atributo y los posteriores en vertical para que coincidan con la sangría del primer atributo. La siguiente prueba XML es un ejemplo de cómo se alinearían los atributos.

```xml
<item id = "123-A"
      name = "hammer"
      price = "9.95">
</item>
```

## <a name="auto-reformat"></a>Formatear automáticamente
 **Al pegar desde el Portapapeles**

 Vuelve a dar formato al texto XML pegado desde el portapapeles.

 **En la realización de la etiqueta de cierre**

 Vuelve a dar formato el elemento cuando se completa la etiqueta de cierre.

## <a name="mixed-content"></a>Contenido mixto
 **Conservar el contenido mixto de forma predeterminada**

 Determina si el editor volverá a dar formato al contenido mixto. De forma predeterminada, el editor intenta volver a dar formato al contenido mixto, excepto cuando el contenido se halla en un ámbito `xml:space="preserve"`.

 Si un elemento contiene una mezcla de texto y marcado, se considera que el contenido es mixto. A continuación se muestra un ejemplo de un elemento con contenido mixto.

```xml
<dir>c:\data\AlphaProject\
  <file readOnly="false">test1.txt</file>
  <file readOnly="false">test2.txt</file>
</dir>
```

## <a name="see-also"></a>Vea también

- [Propiedades de documentos XML, Ventana Propiedades](../xml-tools/xml-document-properties-properties-window.md)
- [Componentes del Editor XML](../xml-tools/xml-editor-components.md)