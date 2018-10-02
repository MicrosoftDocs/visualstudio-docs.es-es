---
title: Crear comentarios de documentación XML para IntelliSense para JavaScript | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- code comments, JavaScript IntelliSense
- XML documentation comments, JavaScript IntelliSense
- documentation comments [JavaScript]
- IntelliSense [JavaScript], XML documentation comments
ms.assetid: a27f5b50-9807-436f-a0cf-6f3137ecbaf0
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 74302bb9aea552bfc4e8fedc93fd7aebc69fb4b2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47582142"
---
# <a name="create-xml-documentation-comments-for-javascript-intellisense"></a>Crear comentarios de documentación XML para IntelliSense para JavaScript
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [documentación de Visual Studio 2017](https://docs.microsoft.com/en-us/visualstudio/).  
  
*Comentarios de documentación XML* son los comentarios de JavaScript que agrega a una secuencia de comandos para proporcionar información sobre los elementos de código como funciones, campos y variables. En Visual Studio, estas descripciones de texto se muestran con IntelliSense cuando se hace referencia la función de script.  
  
 En este tema se proporciona un tutorial básico sobre el uso de comentarios de documentación XML. Para obtener información sobre el uso de otros elementos, tales como [ \<var >](../ide/var-javascript.md) y [ \<valor >](../ide/value-javascript.md)y para obtener ejemplos de código adicional, vea [comentarios de documentación XML ](../ide/xml-documentation-comments-javascript.md). Para obtener información acerca de cómo proporcionar información de IntelliSense para una devolución de llamada asincrónica, como un `Promise`, consulte [ \<devuelve >](../ide/returns-javascript.md).  
  
> [!NOTE]
>  Los comentarios de documentación XML únicamente están disponibles en los archivos, ensamblados y servicios a los que se hace referencia.  
  
### <a name="to-create-xml-documentation-comments-for-a-javascript-function"></a>Para crear comentarios de documentación XML para una función de JavaScript  
  
-   En la función, agregue [ \<resumen >](../ide/summary-javascript.md), [ \<param >](../ide/param-javascript.md), y [ \<devuelve >](../ide/returns-javascript.md) elementos y delante de cada elemento con tres diagonales (/ / /).  
  
    > [!NOTE]
    >  Cada elemento debe estar en una sola línea.  
  
     El ejemplo siguiente muestra una función de JavaScript.  
  
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
  
-   Para ver los comentarios de documentación XML, escriba el nombre y el paréntesis de apertura de una función marcada con comentarios de documentación XML, como se muestra en el ejemplo siguiente:  
  
    ```javascript  
    var areaVal = getArea(  
    ```  
  
     Al escribir el paréntesis de apertura de la función que contiene los comentarios de documentación XML, el Editor de código usa IntelliSense para mostrar la información que se define en los comentarios de documentación XML.  
  
### <a name="to-create-xml-documentation-comments-for-a-javascript-field"></a>Para crear comentarios de documentación XML para un campo de JavaScript  
  
-   En una definición de función o el objeto de constructor, agregue un [ \<campo >](../ide/field-javascript.md) elemento precedido por tres barras diagonales (/ / /).  
  
     El ejemplo siguiente muestra el uso de la `<field>` elemento en una función constructora. Para obtener ejemplos adicionales, consulte [ \<campo >](../ide/field-javascript.md).  
  
    ```javascript  
    function Engine() {  
        /// <field name='HorsePower' type='Number'>The engine's horsepower.</field>  
        this.HorsePower = 150;  
    }  
    ```  
  
-   Para ver los comentarios de documentación XML, crear un objeto utilizando el constructor de función que está marcado con comentarios de documentación XML, como se muestra en el ejemplo siguiente.  
  
    ```javascript  
    var eng = new Engine();  
    ```  
  
-   En la línea siguiente, escriba el nombre del objeto y un período para mostrar información de IntelliSense para el campo.  
  
    ```javascript  
    eng.  
    ```  
  
### <a name="to-create-xml-documentation-comments-for-an-overloaded-function"></a>Para crear comentarios de documentación XML para una función sobrecargada  
  
1.  En la función, agregue un [ \<firma >](../ide/signature-javascript.md) (elemento) para cada sobrecarga. En estos elementos, agregue otros elementos, tales como `<summary>`, `<param>`, y `<returns>`, delante de cada elemento con tres barras diagonales (/ / /).  
  
     El ejemplo siguiente muestra una función sobrecargada de JavaScript. En este ejemplo, las sobrecargas difieren según el tipo de parámetro.  
  
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
  
2.  Para ver los comentarios de documentación XML, escriba el nombre y el paréntesis de apertura de la función que está marcado con comentarios de documentación XML, como se muestra en el ejemplo siguiente:  
  
    ```javascript  
    calc(  
    ```  
  
### <a name="to-create-localized-intellisense"></a>Para crear IntelliSense localizado  
  
1.  Cree un archivo XML que tenga comentarios de documentación en el formato OpenAjax MessageBundle.  
  
    > [!IMPORTANT]
    >  El formato recomendado es de MessageBundle. Este formato no se admite en Microsoft Ajax o en archivos de winmd. Para obtener información sobre cómo usar la alternativa `VSDoc` de formato, vea [ \<loc >](../ide/loc-javascript.md).  
  
     El ejemplo siguiente se muestra el contenido en un archivo asociado que contiene la información de IntelliSense localizada. Se trata de un archivo XML que se encuentra en una carpeta de referencia cultural específica, como JA. La carpeta debe estar en la misma ubicación que el archivo .js que contiene el `<loc>` elemento. El nombre de archivo del archivo XML debe coincidir con el `filename` los parámetros especificados en el `<loc>` elemento.  
  
    ```  
    <messagebundle>  
      <msg name="1">A class that represents a rectangle</msg>  
      <msg name="2">The length of the rectangle</msg>  
      <msg name="3">The height of the rectangle</msg>  
    </messagebundle>  
  
    ```  
  
2.  En el archivo .js, agregue el código siguiente. El `<loc>` elemento se debe declarar antes que cualquier script y sigue las mismas reglas de uso como el `<reference>` elemento. Para obtener más información, consulte [IntelliSense para JavaScript](../ide/javascript-intellisense.md) y [ \<loc >](../ide/loc-javascript.md).  
  
    ```javascript  
    /// <loc filename="messageFilename.xml" format="messagebundle"/>  
  
    ```  
  
3.  En el archivo .js, agregue los elementos de documentación XML y descripciones de forma predeterminada. Establecer el `locid` valores para que coincida con los correspondientes del atributo `name` valores de atributo de archivo asociado. Las descripciones predeterminadas se reemplazará por la información de IntelliSense localizada, si está disponible.  
  
    ```javascript  
    function add(a,b)   
    {  
        /// <summary locid='1'>description</summary>  
        /// <param name='a' locid='2'>parameter a description</param>  
        /// <param name='b' locid='3'>parameter b description</param>  
    }  
  
    ```  
  
4.  Para ver los comentarios de documentación XML, escriba el nombre y el paréntesis de apertura de la función, como en el ejemplo siguiente:  
  
    ```javascript  
    add(  
    ```  
  
## <a name="see-also"></a>Vea también  
 [IntelliSense para JavaScript](../ide/javascript-intellisense.md)   
 [Comentarios de documentación XML](../ide/xml-documentation-comments-javascript.md)   
 [NIB: Tutorial: JavaScript IntelliSense en ASP.NET](http://msdn.microsoft.com/en-us/4f6e0cc2-7f48-4dbf-abb0-7fb743a2d05b)



