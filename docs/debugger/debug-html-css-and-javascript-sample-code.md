---
title: "Depurar c&#243;digo de ejemplo HTML, CSS y JavaScript | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 51893967-98c8-4141-ba40-03646f221760
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Depurar c&#243;digo de ejemplo HTML, CSS y JavaScript
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

![Se aplica a Windows y a Windows Phone](../debugger/media/windows_and_phone_content.png "windows\_and\_phone\_content")  
  
 El código de este tema es el archivo de ejemplo para [Inicio rápido: Depurar HTML y CSS](../debugger/quickstart-debug-html-and-css.md).  Los errores presentes por diseño en el tutorial rápido se corrigen en esta versión del código.  
  
## Código de ejemplo  
 El siguiente código HTML se usa en la etiqueta \<body\> del Inicio rápido.  
  
```html  
<div id="flipTemplate" data-win-control="WinJS.Binding.Template"  
         style="display:none">  
    <div class="fixedItem" >  
        <img src="#" data-win-bind="src: flipImg" />  
    </div>  
</div>  
<div id="fView" data-win-control="WinJS.UI.FlipView" data-win-options="{  
    itemDataSource: Data.items.dataSource, itemTemplate: flipTemplate }">  
</div>  
```  
  
 El código CSS siguiente muestra las adiciones realizadas a default.css.  
  
```css  
#fView {  
    background-color:#0094ff;  
    height: 500px;  
    margin: 25px;  
}  
```  
  
 En el ejemplo de código siguiente se muestra el código de JavaScript completo de default.js.  Las referencias a los espacios de nombres de WinJS para este código están en el archivo default.html de la plantilla.  
  
```javascript  
(function () {  
    "use strict";  
  
    var app = WinJS.Application;  
    var activation = Windows.ApplicationModel.Activation;  
  
    var myData = [];  
    for (var x = 0; x < 4; x++) {  
        myData[x] = { flipImg: "/images/logo.png" }  
    };  
  
    var pages = new WinJS.Binding.List(myData, { proxy: true });  
  
    app.onactivated = function (args) {  
        if (args.detail.kind === activation.ActivationKind.launch) {  
            if (args.detail.previousExecutionState !==  
            activation.ApplicationExecutionState.terminated) {  
                // TODO: . . .  
            } else {  
                // TODO: . . .  
            }  
            args.setPromise(WinJS.UI.processAll());  
  
            updateImages();  
        }  
    };  
  
    function updateImages() {  
  
        pages.setAt(0, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223195" });  
        pages.setAt(1, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223196" });  
        pages.setAt(2, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223197" });  
    };  
  
    app.oncheckpoint = function (args) {  
    };  
  
    app.start();  
  
    var publicMembers = {  
        items: pages  
    };  
  
    WinJS.Namespace.define("Data", publicMembers);  
  
})();  
```  
  
## Vea también  
 [Inicio rápido: Depurar HTML y CSS](../debugger/quickstart-debug-html-and-css.md)