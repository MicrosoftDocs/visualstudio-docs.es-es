---
title: Depuración de código de ejemplo HTML y CSS | Microsoft Docs
description: Encuentre el código de ejemplo HTML y CSS que se usa con un artículo de inicio rápido sobre la depuración. Los errores presentes por diseño en el inicio rápido están corregidos en este artículo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 51893967-98c8-4141-ba40-03646f221760
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 14d071d4ab47efd60aa31ecbffe1d7cb873ac6fd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99865610"
---
# <a name="debug-html-and-css-sample-code"></a>Depurar código de ejemplo HTML y CSS

El código de este tema es el archivo de ejemplo para [Inicio rápido: Depurar HTML y CSS](../debugger/quickstart-debug-html-and-css.md). Los errores presentes por diseño en el tutorial rápido se corrigen en esta versión del código.

## <a name="sample-code"></a>Código de ejemplo
El siguiente código HTML se usa en la etiqueta \<body> del Inicio rápido.

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

En el ejemplo de código siguiente se muestra el código de JavaScript completo de default.js. Las referencias a los espacios de nombres de WinJS para este código están en el archivo default.html de la plantilla.

```javascript
(function () {
    "use strict";

    var app = WinJS.Application;
    var activation = Windows.ApplicationModel.Activation;

    var myData = [];
    for (var x = 0; x < 3; x++) {
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

        pages.setAt(0, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-76.jpg" });
        pages.setAt(1, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-77.jpg" });
        pages.setAt(2, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-78.jpg" });
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

## <a name="see-also"></a>Vea también
- [Inicio rápido: depuración de HTML y CSS](../debugger/quickstart-debug-html-and-css.md)
