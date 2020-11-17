---
title: Examinen de nodos mediante la vista Modelo de contenido en el diseñador de esquemas XML
description: Aprenda a usar la vista Modelo de contenido del Diseñador de esquemas XML para examinar el modelo de contenido de los nodos de un esquema XML.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c42ddac8-b0e3-48d6-9832-112a19d6c104
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ef330e6e189b9cee1126d5de48d55622fe8d9046
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2020
ms.locfileid: "93399514"
---
# <a name="how-to-examine-the-content-model-of-nodes-using-the-content-model-view"></a>Procedimiento Examinación del modelo de contenido de los nodos mediante la vista Modelo de contenido

En este tema se explica cómo explorar los nodos mediante la [vista Modelo de contenido](../xml-tools/content-model-view.md).

## <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>Para crear un nuevo archivo XSD y mostrar el elemento raíz en el vista Modelo de contenido

1. Cree un nuevo archivo de esquema XML.

2. Haga clic en **Use el Editor XML para ver y editar el archivo de esquema XML subyacente** en la vista Inicio.

3. Copie el código de ejemplo del esquema XML desde el [esquema XML de ejemplo: esquema de pedido de compra](../xml-tools/sample-xsd-file-purchase-order-schema.md) y péguelo para reemplazar el código que se agregó de forma predeterminada al nuevo archivo XSD.

4. Seleccione el elemento `purchaseOrder` en el Explorador de esquemas haciendo clic con el botón derecho en el elemento `purchaseOrder` en el editor XML y seleccionando **Mostrar en el Explorador de esquemas XML**.

5. Haga clic con el botón derecho en `purchaseOrder` dentro del Explorador XML y seleccione **Mostrar en la vista Modelo de contenido**.

     La vista Modelo de contenido muestra el elemento `purchaseOrder` en la superficie de diseño.

6. Expanda los nodos `shipTo`, `billTo` y `items` haciendo doble clic en cada nodo o haciendo clic en la flecha doble situada a la derecha de cada nodo.

     Los nodos del elemento `purchaseOrder` se expanden y puede ver el modelo de contenido del elemento.

7. Haga clic en cualquier nodo situado debajo del elemento `purchaseOrder` y busque en la barra de ruta de navegación dónde se encuentra el nodo seleccionado dentro del conjunto de esquemas.

8. Haga clic en el botón **Mostrar documentación** en la barra de herramientas XSD para ver la documentación. También puede hacer clic con el botón secundario en la superficie de diseño para ver la documentación.

9. Haga clic con el botón derecho en el nodo `purchaseOrder` y seleccione **Generar XML de muestra** para ver el documento de instancia XML.
