---
title: Opciones, editor de texto, XML y formato
ms.date: 10/29/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Formatting
ms.assetid: 203e60b2-7b80-4ff4-9fa1-aa9f4374377b
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 652d9ff3b2178089b4ef35838a4181408aef7f09
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/27/2018
ms.locfileid: "52388304"
---
# <a name="options-text-editor-xml-formatting"></a>Opciones, editor de texto, XML y formato

Use la página de propiedades **Formato** para especificar cómo se aplica formato a los elementos y atributos en los documentos XML. Para abrir el cuadro de diálogo **Opciones**, haga clic en el menú **Herramientas** y, después, en **Opciones**. Para acceder a la página de propiedades **Formato**, expanda el nodo **Editor de texto** > **XML** > **Formato**.

## <a name="attributes"></a>Atributos

**Preservar el formato manual de atributos**

No cambia el formato de los atributos. Esta opción es el valor predeterminado.

> [!NOTE]
> Si los atributos están en varias líneas, el editor aplica sangría a cada línea de atributos para que coincida con la sangría del elemento primario.

**Alinear los atributos en líneas separadas**

Alinea el segundo atributo y los posteriores en vertical para que coincidan con la sangría del primer atributo. La siguiente prueba XML es un ejemplo de cómo se alinearían los atributos.

```xml
<item id = "123-A"
      name = "hammer"
      price = "9.95">
</item>
```

## <a name="auto-reformat"></a>Formatear automáticamente

**Al pegar del Portapapeles**

Cambia el formato del texto XML pegado desde el Portapapeles.

**Al terminar la etiqueta final**

Cambia el formato del elemento cuando se completa la etiqueta de cierre.

## <a name="mixed-content"></a>Contenido mixto

**Aplicar formato al contenido mixto de forma predeterminada**

Intenta cambiar el formato del contenido mixto, excepto cuando este se halla en un ámbito `xml:space="preserve"`. Esta opción es el valor predeterminado.

Si un elemento contiene una mezcla de texto y marcado, se considera que el contenido es mixto. A continuación se muestra un ejemplo de un elemento con contenido mixto.

```xml
<dir>c:\data\AlphaProject\
  <file readOnly="false">test1.txt</file>
  <file readOnly="false">test2.txt</file>
</dir>
```

## <a name="see-also"></a>Vea también

- [Cómo: Crear documentación XML en Visual Basic](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation)
- [Generación de código](../code-generation-in-visual-studio.md)