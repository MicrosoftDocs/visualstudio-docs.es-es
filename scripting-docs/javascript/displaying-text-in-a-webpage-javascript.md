---
title: "Mostrar texto en una página web (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- JavaScript, write
- JavaScript, writing text
ms.assetid: 3c2455e7-2402-45f2-9545-77a2b2490527
caps.latest.revision: 30
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: a8c9ea9d0e0300a0d9b71b0b33d7c99c9ac3935c
ms.contentlocale: es-es
ms.lasthandoff: 08/11/2017

---
# <a name="displaying-text-in-a-webpage-javascript"></a>Mostrar texto en una página web (JavaScript)
Hay varias maneras de mostrar texto en una página web. Cada una tiene sus ventajas y desventajas y admite usos concretos.  
  
## <a name="displaying-text"></a>Mostrar texto  
  
-   La manera recomendada de mostrar texto es crear un elemento y escribir en su propiedad textContent.  
  
    ```JavaScript  
    <div id="textDiv"></div>  
    <script type="text/javascript">  
        var div = document.getElementById("textDiv");  
        div.textContent = "my text";  
        var text = div.textContent;  
    </script>  
    ```  
  
     En este ejemplo, el valor de `text` es "my text". Sin embargo, el valor resultante de obtener o establecer la propiedad `textContent` en un nodo principal podría incluir contenido textual de los elementos secundarios del nodo. En el ejemplo siguiente se muestra que la propiedad `textContent` que se establece en un nodo secundario se incluye en el valor de `textContent` del nodo principal:  
  
    ```JavaScript  
    <div id="textDiv">  
        <div id="nested"></div>  
    </div>  
    <script type="text/javascript">  
        var div = document.getElementById("textDiv");  
        var nestedDiv = document.getElementById("nested");  
        nestedDiv.textContent = "nested";  
  
        var text = "[" + div.textContent + "]";  
    </script>  
    ```  
  
     En este ejemplo, el valor de `text` es "[nested]".  
  
-   También puede crear un elemento y escribir en sus propiedades [innerHTML](http://msdn.microsoft.com/library/ie/ms533897\(v=vs.85\).aspx) o [innerText](http://msdn.microsoft.com/library/ie/ms533899\(v=vs.85\).aspx). El establecimiento de estas propiedades afecta solo al texto del propio elemento, no al de sus elementos secundarios. Sin embargo, estas propiedades también presentan algunos inconvenientes:  
  
    -   La propiedad [innerText](http://msdn.microsoft.com/library/ie/ms533899\(v=vs.85\).aspx) no funciona en todos los exploradores, por lo que quizás desee evitarla por motivos de compatibilidad.  
  
    -   En la propiedad [innerText](http://msdn.microsoft.com/library/ie/ms533899\(v=vs.85\).aspx) influyen los estilos CSS y no aparece si el elemento está oculto.  
  
    -   La propiedad [innerHTML](http://msdn.microsoft.com/library/ie/ms533897\(v=vs.85\).aspx) obtiene y establece texto y nodos anidados. Si no se protege, podría ser utilizada en ataques de inyección de script. Además, si se establece en texto sin etiquetas HTML, se quitan todos los nodos establecidos anteriormente.  
  
-   Puede usar el método `document.write` sin tener que crear un elemento. Sin embargo, el uso de este método hace que se borre toda la página web y posiblemente no sea esto lo que desea.  
  
     En el ejemplo siguiente se muestra una de las desventajas de utilizar `document.write`. El script tiene por objeto mostrar la hora cada 5 segundos, pero muestra la hora solo dos veces. Para cuando se llama a `document.write` por segunda vez, la página ha terminado de cargarse y `document.write` borra entonces la página completa (llama a `document.open`). En este momento, la función `ShowTime` ya no existe.  
  
    ```html  
    <!DOCTYPE html>  
    <html>  
    <head>  
    <script type="text/javascript">  
        function ShowTime()  
        {  
            var dt = new Date();  
            document.write(dt.toTimeString());  
            // var elem = document.getElementById("divElem");  
            // elem.textContent = dt.toTimeString();  
            window.setTimeout("ShowTime();", 5000);  
        }  
    </script>  
    </head>  
  
    <body>  
    <script type="text/javascript">  
        ShowTime();  
    </script>  
    <div id="myDiv"></div>  
    </body>  
    </html>  
  
    ```  
  
     Para corregir el código anterior, quite la línea de código que contiene `document.write` y quite los comentarios de las dos líneas comentadas de código que aparecen a continuación.  
  
-   También puede utilizar una función `alert``prompt` o `confirm`, que muestra un mensaje en una ventana emergente. En la mayoría de los casos no es conveniente usar una ventana emergente en un explorador web. La mayoría de los exploradores modernos tienen valores de configuración que bloquean automáticamente las ventanas emergentes, por lo que no se podrá ver su mensaje. Además, es posible que se cree un bucle infinito al usar ventanas emergentes, que impide que el usuario cierre la página web de la manera habitual.
