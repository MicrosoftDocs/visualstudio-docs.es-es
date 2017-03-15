---
title: "C&#243;mo: Crear comentarios de documentaci&#243;n XML de JavaScript | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "comentarios en código, IntelliSense para JavaScript"
  - "comentarios de documentación [JavaScript]"
  - "IntelliSense [JavaScript], comentarios de documentación XML"
  - "comentarios de documentación XML, IntelliSense para JavaScript"
ms.assetid: a27f5b50-9807-436f-a0cf-6f3137ecbaf0
caps.latest.revision: 15
caps.handback.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# C&#243;mo: Crear comentarios de documentaci&#243;n XML de JavaScript
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

*Comentarios de documentación XML* son los comentarios de JavaScript que agregar a una secuencia de comandos para proporcionar información acerca de los elementos de código, como las funciones, campos y las variables.  En Visual Studio, estas descripciones de texto se muestran con IntelliSense cuando se hace referencia la función de secuencia de comandos.  
  
 Este tema proporciona un tutorial básico sobre el uso de comentarios de documentación XML.  Para obtener información acerca de cómo utilizar otros elementos, tales como [\<var\>](../ide/var-javascript.md) y [\<value\>](../ide/value-javascript.md)y para obtener ejemplos de código adicional, consulte [Comentarios de documentación XML](../ide/xml-documentation-comments-javascript.md).  Para obtener información acerca de cómo proporcionar información de IntelliSense de devolución de llamada asincrónica, como un `Promise`, consulte [\<returns\>](../ide/returns-javascript.md).  
  
> [!NOTE]
>  Comentarios de documentación XML están disponibles sólo en los servicios, los ensamblados y archivos que se hace referencia.  
  
### Para crear comentarios de documentación XML para una función de JavaScript  
  
-   En la función, agregue [\<summary\>](../ide/summary-javascript.md), [\<param\>](../ide/param-javascript.md), y [\<returns\>](../ide/returns-javascript.md) elementos y delante de cada elemento con tres signos de barra diagonal \(\/ \/ \/\).  
  
    > [!NOTE]
    >  Cada elemento debe estar en una sola línea.  
  
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
  
-   Para ver los comentarios de documentación XML, escriba el nombre y el paréntesis de apertura de una función marcada con comentarios de documentación XML, como en el ejemplo siguiente:  
  
    ```javascript  
    var areaVal = getArea(  
    ```  
  
     Al escribir el paréntesis de apertura de la función que contiene los comentarios de documentación XML, en el Editor de código se utiliza IntelliSense para mostrar la información que se define en los comentarios de documentación XML.  
  
### Para crear comentarios de documentación XML para un campo de JavaScript  
  
-   En una definición de objeto o función de constructor, agregue un [\<field\>](../ide/field-javascript.md) elemento precedidos por tres signos de barra diagonal \(\/ \/ \/\).  
  
     En el ejemplo siguiente se muestra el uso de la `<field>` elemento de una función constructora.  Para obtener otros ejemplos, vea [\<field\>](../ide/field-javascript.md).  
  
    ```javascript  
    function Engine() {  
        /// <field name='HorsePower' type='Number'>The engine's horsepower.</field>  
        this.HorsePower = 150;  
    }  
    ```  
  
-   Para ver los comentarios de documentación XML, crear un objeto con el constructor de la función que está marcado con comentarios de documentación XML, como en el ejemplo siguiente.  
  
    ```javascript  
    var eng = new Engine();  
    ```  
  
-   En la siguiente línea, escriba el nombre del objeto y un período para mostrar la información de IntelliSense para el campo.  
  
    ```javascript  
    eng.  
    ```  
  
### Para crear comentarios de documentación XML para una función sobrecargada  
  
1.  En la función, agregue un [\<signature\>](../ide/signature-javascript.md) \(elemento\) para cada sobrecarga.  En estos elementos, agregar otros elementos, tales como `<summary>`, `<param>`, y `<returns>`, anterior a cada elemento con tres diagonales \(\/ \/ \/\).  
  
     En el ejemplo siguiente se muestra una función sobrecargada de JavaScript.  En este ejemplo, las sobrecargas se diferencian por el tipo de parámetro.  
  
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
  
2.  Para ver los comentarios de documentación XML, escriba el nombre y el paréntesis de apertura de la función que está marcada con comentarios de documentación XML, como en el ejemplo siguiente:  
  
    ```javascript  
    calc(  
    ```  
  
### Para crear IntelliSense localizada  
  
1.  Crear un archivo XML que tiene comentarios de documentación en el formato de OpenAjax MessageBundle.  
  
    > [!IMPORTANT]
    >  MessageBundle es el formato recomendado.  Este formato no es compatible con Ajax de Microsoft o en los archivos de .winmd.  Para obtener información acerca del uso de la alternativas `VSDoc` de formato, vea [\<loc\>](../ide/loc-javascript.md).  
  
     En el ejemplo siguiente se muestra contenido en un archivo sidecar que contiene la información de IntelliSense localizada.  Se trata de un archivo XML que se encuentra en una carpeta específica de la referencia cultural, como JA.  La carpeta debe estar en la misma ubicación que el archivo .js que contiene el `<loc>` elemento.  El nombre de archivo del archivo XML debe coincidir con el `filename` parámetro especificado en la `<loc>` elemento.  
  
    ```  
    <messagebundle>  
      <msg name="1">A class that represents a rectangle</msg>  
      <msg name="2">The length of the rectangle</msg>  
      <msg name="3">The height of the rectangle</msg>  
    </messagebundle>  
  
    ```  
  
2.  En el archivo .js, agregue el código siguiente.  El `<loc>` elemento se debe declarar antes de cualquier secuencia de comandos y sigue las mismas reglas de uso como la `<reference>` elemento.  Para obtener más información, vea [IntelliSense para JavaScript](../ide/javascript-intellisense.md) y [\<loc\>](../ide/loc-javascript.md).  
  
    ```javascript  
    /// <loc filename="messageFilename.xml" format="messagebundle"/>  
  
    ```  
  
3.  En el archivo .js, agregue los elementos de documentación XML y las descripciones de predeterminado.  Establecer el `locid` valores para que coincida con el correspondiente del atributo `name` los valores de atributo del archivo sidecar.  Las descripciones de predeterminado se reemplazará por información localizada de IntelliSense, si está disponible.  
  
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
  
## Vea también  
 [IntelliSense para JavaScript](../ide/javascript-intellisense.md)   
 [Comentarios de documentación XML](../ide/xml-documentation-comments-javascript.md)   
 [NIB: Walkthrough: JavaScript IntelliSense in ASP.NET](http://msdn.microsoft.com/es-es/4f6e0cc2-7f48-4dbf-abb0-7fb743a2d05b)