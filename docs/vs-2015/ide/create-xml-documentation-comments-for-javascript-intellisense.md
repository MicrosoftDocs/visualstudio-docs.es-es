---
title: Creación de comentarios de documentación XML para IntelliSense para JavaScript | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code comments, JavaScript IntelliSense
- XML documentation comments, JavaScript IntelliSense
- documentation comments [JavaScript]
- IntelliSense [JavaScript], XML documentation comments
ms.assetid: a27f5b50-9807-436f-a0cf-6f3137ecbaf0
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 21fdc15b161b7d1cef30effe82e518a174bc9666
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72619547"
---
# <a name="create-xml-documentation-comments-for-javascript-intellisense"></a>Crear comentarios de documentación XML para IntelliSense para JavaScript
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los *comentarios de documentación XML* son comentarios de JavaScript que se agregan a un script para proporcionar información sobre elementos de código como funciones, campos y variables. En Visual Studio, estas descripciones de texto se muestran con IntelliSense cuando se hace referencia a la función de script.

 En este tema se proporciona un tutorial básico sobre el uso de comentarios de documentación XML. Para obtener información sobre el uso de otros elementos, como [\<var>](../ide/var-javascript.md) y [\<value>](../ide/value-javascript.md) , y para obtener ejemplos de código adicionales, vea los [comentarios de documentación XML](../ide/xml-documentation-comments-javascript.md). Para obtener información sobre cómo proporcionar información de IntelliSense para una devolución de llamada asincrónica como `Promise` , vea [\<returns>](../ide/returns-javascript.md) .

> [!NOTE]
> Los comentarios de documentación XML únicamente están disponibles en los archivos, ensamblados y servicios a los que se hace referencia.

### <a name="to-create-xml-documentation-comments-for-a-javascript-function"></a>Para crear comentarios de documentación XML para una función de JavaScript

- En la función, agregue [\<summary>](../ide/summary-javascript.md) [\<param>](../ide/param-javascript.md) [\<returns>](../ide/returns-javascript.md) los elementos, y, y precedan a cada elemento con tres marcas de barra diagonal (///).

    > [!NOTE]
    > Cada elemento debe estar en una sola línea.

     En el ejemplo siguiente se muestra una función de JavaScript.

    ```javascript
    function getArea(radius)
    {
        /// <summary>Determines the area of a circle that has the specified radius parameter.</summary>
        /// <param name="radius" type="Number">The radius of the circle.</param>
        /// <returns type="Number">The area.</returns>
        var areaVal;
        areaVal = Math.PI * radius * radius;
        return areaVal;
    }
    ```

- Para ver los comentarios de documentación XML, escriba el nombre y el paréntesis de apertura de una función marcada con comentarios de documentación XML, como en el ejemplo siguiente:

    ```javascript
    var areaVal = getArea(
    ```

     Al escribir el paréntesis de apertura de la función que contiene los comentarios de documentación XML, el editor de código utiliza IntelliSense para mostrar la información que se define en los comentarios de documentación XML.

### <a name="to-create-xml-documentation-comments-for-a-javascript-field"></a>Para crear comentarios de documentación XML para un campo de JavaScript

- En una función de constructor o definición de objeto, agregue un [\<field>](../ide/field-javascript.md) elemento precedido por tres marcas de barra diagonal (///).

     En el ejemplo siguiente se muestra el uso del `<field>` elemento en una función constructora. Para obtener más ejemplos, vea [\<field>](../ide/field-javascript.md) .

    ```javascript
    function Engine() {
        /// <field name='HorsePower' type='Number'>The engine's horsepower.</field>
        this.HorsePower = 150;
    }
    ```

- Para ver los comentarios de documentación XML, cree un objeto utilizando el constructor de función que está marcado con comentarios de documentación XML, como en el ejemplo siguiente.

    ```javascript
    var eng = new Engine();
    ```

- En la línea siguiente, escriba el nombre del objeto y un punto para mostrar la información de IntelliSense para el campo.

    ```javascript
    eng.
    ```

### <a name="to-create-xml-documentation-comments-for-an-overloaded-function"></a>Para crear comentarios de documentación XML para una función sobrecargada

1. En la función, agregue un [\<signature>](../ide/signature-javascript.md) elemento para cada sobrecarga. En estos elementos, agregue otros elementos, como `<summary>` , `<param>` y `<returns>` , delante de cada elemento con tres marcas de barra diagonal (///).

     En el ejemplo siguiente se muestra una función de JavaScript sobrecargada. En este ejemplo, las sobrecargas se diferencian por el tipo de parámetro.

    ```javascript
    function calc(a) {
        /// <signature>
        /// <summary>Function summary 1.</summary>
        /// <param name="a" type="Number">A number.</param>
        /// <returns type="Number" />
        /// </signature>
        /// <signature>
        /// <summary>Function summary 2.</summary>
        /// <param name="a" type="String">A string.</param>
        /// <returns type="Number" />
        /// </signature>
        return a;
    }
    ```

2. Para ver los comentarios de documentación XML, escriba el nombre y el paréntesis de apertura de la función que se marca con comentarios de documentación XML, como en el ejemplo siguiente:

    ```javascript
    calc(
    ```

### <a name="to-create-localized-intellisense"></a>Para crear IntelliSense adaptado

1. Cree un archivo XML que tenga comentarios de documentación en el formato OpenAjax MessageBundle.

    > [!IMPORTANT]
    > MessageBundle es el formato recomendado. Este formato no se admite en Microsoft Ajax o en archivos. winmd. Para obtener información acerca del uso del `VSDoc` formato alternativo, vea [\<loc>](../ide/loc-javascript.md) .

     En el ejemplo siguiente se muestra el contenido de un archivo sidecar que contiene la información de IntelliSense localizada. Se trata de un archivo XML que se encuentra en una carpeta específica de la referencia cultural, como JA. La carpeta debe estar en la misma ubicación que el archivo. js que contiene el `<loc>` elemento. El nombre de archivo del archivo XML debe coincidir con el `filename` parámetro especificado en el `<loc>` elemento.

    ```
    <messagebundle>
      <msg name="1">A class that represents a rectangle</msg>
      <msg name="2">The length of the rectangle</msg>
      <msg name="3">The height of the rectangle</msg>
    </messagebundle>

    ```

2. En el archivo. js, agregue el código siguiente. El `<loc>` elemento debe declararse antes que cualquier script y sigue las mismas reglas de uso que el `<reference>` elemento. Para obtener más información, vea [IntelliSense para JavaScript](../ide/javascript-intellisense.md) y [\<loc>](../ide/loc-javascript.md) .

    ```javascript
    /// <loc filename="messageFilename.xml" format="messagebundle"/>

    ```

3. En el archivo. js, agregue los elementos de documentación XML y las descripciones predeterminadas. Establezca los `locid` valores de atributo para que coincidan con los `name` valores de atributo correspondientes del archivo sidecar. Las descripciones predeterminadas se reemplazarán por la información de IntelliSense localizada, si está disponible.

    ```javascript
    function add(a,b)
    {
        /// <summary locid='1'>description</summary>
        /// <param name='a' locid='2'>parameter a description</param>
        /// <param name='b' locid='3'>parameter b description</param>
    }

    ```

4. Para ver los comentarios de documentación XML, escriba el nombre y el paréntesis de apertura de la función, como en el ejemplo siguiente:

    ```javascript
    add(
    ```

## <a name="see-also"></a>Consulte también
 [JavaScript IntelliSense](../ide/javascript-intellisense.md) [Comentarios de documentación XML](../ide/xml-documentation-comments-javascript.md) [de IntelliSense para JavaScript NIB: Tutorial: IntelliSense para JavaScript en ASP.net](https://msdn.microsoft.com/4f6e0cc2-7f48-4dbf-abb0-7fb743a2d05b)
