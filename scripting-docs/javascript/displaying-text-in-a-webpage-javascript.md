---
title: "Mostrar texto en una p&#225;gina web (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "JavaScript, escritura"
  - "JavaScript, escribir texto"
ms.assetid: 3c2455e7-2402-45f2-9545-77a2b2490527
caps.latest.revision: 30
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 27
---
# Mostrar texto en una p&#225;gina web (JavaScript)
Hay varias maneras de mostrar texto en una página web.  Cada una tiene ventajas y desventajas y admite usos concretos.  
  
## Mostrar texto  
  
-   La manera recomendada de mostrar texto es crear un elemento y escribir en su propiedad [textContent](http://msdn.microsoft.com/es-es/e530667f-f8fa-4b6d-a47c-4d5c75e71265):  
  
    ```javascript  
    <div id="textDiv"></div>  
    <script type="text/javascript">  
        var div = document.getElementById("textDiv");  
        div.textContent = "my text";  
        var text = div.textContent;  
    </script>  
    ```  
  
     En este ejemplo, el valor de `text` es "my text".  Sin embargo, el valor resultante de obtener o establecer la propiedad [textContent](http://msdn.microsoft.com/es-es/e530667f-f8fa-4b6d-a47c-4d5c75e71265) en un nodo primario podría incluir contenido textual de los elementos secundarios del nodo.  En el ejemplo siguiente se muestra que el valor de [textContent](http://msdn.microsoft.com/es-es/e530667f-f8fa-4b6d-a47c-4d5c75e71265) establecido en un nodo secundario está incluido en el valor de [textContent](http://msdn.microsoft.com/es-es/e530667f-f8fa-4b6d-a47c-4d5c75e71265) del nodo primario:  
  
    ```javascript  
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
  
     En este ejemplo, el valor de `text` es "\[nested\]".  
  
-   También puede crear un elemento y escribir en sus propiedades [innerHTML](http://msdn.microsoft.com/library/ie/ms533897\(v=vs.85\).aspx) o [innerText](http://msdn.microsoft.com/library/ie/ms533899\(v=vs.85\).aspx).  El hecho de establecer estas propiedades solo afecta al texto del propio elemento, no a sus elementos secundarios.  Sin embargo, estas propiedades también tienen algunas desventajas:  
  
    -   La propiedad [innerText](http://msdn.microsoft.com/library/ie/ms533899\(v=vs.85\).aspx) no funciona en todos los exploradores, por lo que tal vez le interese evitarla por cuestiones de compatibilidad.  
  
    -   La propiedad [innerText](http://msdn.microsoft.com/library/ie/ms533899\(v=vs.85\).aspx) se ve afectada por los estilos CSS y no aparece si el elemento está oculto.  
  
    -   La propiedad [innerHTML](http://msdn.microsoft.com/library/ie/ms533897\(v=vs.85\).aspx) obtiene y establece los nodos anidados y el texto.  Si no se protege, podría usarse para ataques por inyección de script.  Además, si se establece como texto sin etiquetas HTML, quita todos los nodos establecidos previamente.  
  
-   Puede usar el método `document.write` sin tener que crear un elemento.  Sin embargo, este método hace que toda la página web se borre, algo que tal vez no le interese.  
  
     En el ejemplo siguiente se muestra una de las desventajas de usar `document.write`.  El script está diseñado para mostrar la hora cada 5 segundos, pero muestra la hora solo dos veces.  En el momento en que se llama a `document.write` la segunda vez, la página terminó de cargarse y `document.write` borra toda la página \(llama a `document.open`\).  En este punto, la función `ShowTime` ya no existe.  
  
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
  
     Para corregir el código anterior, quite la línea de código que contiene `document.write` y quite los comentarios de las dos líneas de código comentadas que se indican a continuación.  
  
-   También puede usar una función `alert`, `prompt` o `confirm`, que muestran un mensaje en una ventana emergente.  En la mayoría de los casos no es aconsejable usar una ventana emergente en un explorador web.  La mayoría de los exploradores modernos están configurados para bloquear automáticamente las ventanas emergentes, por lo que el mensaje podría no aparecer.  Además, es posible escribir un bucle infinito al usar ventanas emergentes, lo que impide que el usuario cierre la página web de la forma habitual.