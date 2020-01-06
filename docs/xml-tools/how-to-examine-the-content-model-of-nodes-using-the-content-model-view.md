---
title: Examinar nodos mediante la vista modelo de contenido en el diseñador de esquemas XML
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c42ddac8-b0e3-48d6-9832-112a19d6c104
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f5a7e6e311a4fbd02973edf94c6eb117f69d6cea
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592716"
---
# <a name="how-to-examine-the-content-model-of-nodes-using-the-content-model-view"></a>Cómo: examinar el modelo de contenido de los nodos mediante la vista modelo de contenido

En este tema se describe cómo explorar los nodos mediante la [vista modelo de contenido](../xml-tools/content-model-view.md).

## <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>Para crear un nuevo archivo XSD y mostrar el elemento raíz en el vista Modelo de contenido

1. Cree un nuevo archivo de esquema XML.

2. Haga clic en **usar el editor XML para ver y editar el archivo de esquema XML subyacente** en la vista Inicio.

3. Copie el código de ejemplo del esquema XML del [esquema XML de ejemplo: esquema de pedido de compra](../xml-tools/sample-xsd-file-purchase-order-schema.md) y péguelo para reemplazar el código que se agregó al nuevo archivo XSD de forma predeterminada.

4. Seleccione el elemento `purchaseOrder` en el explorador de esquemas haciendo clic con el botón secundario en el elemento `purchaseOrder` en el editor XML y seleccionando **Mostrar en el explorador XML**.

5. Haga clic con el botón secundario en el `purchaseOrder` en el explorador XML y seleccione **Mostrar en la vista modelo de contenido**.

     La vista Modelo de contenido muestra el elemento `purchaseOrder` en la superficie de diseño.

6. Expanda los nodos `shipTo`, `billTo` y `items` haciendo doble clic en cada nodo o haciendo clic en la flecha doble situada a la derecha de cada nodo.

     Los nodos del elemento `purchaseOrder` se expanden y puede ver el modelo de contenido del elemento.

7. Haga clic en cualquier nodo situado debajo del elemento `purchaseOrder` y busque en la barra de ruta de navegación dónde se encuentra el nodo seleccionado dentro del conjunto de esquemas.

8. Haga clic en el botón **Mostrar documentación** de la barra de herramientas XSD para alternar la documentación. También puede hacer clic con el botón secundario en la superficie de diseño para ver la documentación.

9. Haga clic con el botón secundario en el nodo `purchaseOrder` y seleccione **generar XML de ejemplo** para ver el documento de instancia XML.
