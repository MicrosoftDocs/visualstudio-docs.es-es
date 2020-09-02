---
title: 'Cómo: examinar el modelo de contenido de los nodos mediante la vista modelo de contenido | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: c42ddac8-b0e3-48d6-9832-112a19d6c104
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ddadcb0fbd772a5638bf6023b8cf6c18fbd270d7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670853"
---
# <a name="how-to-examine-the-content-model-of-nodes-using-the-content-model-view"></a>Cómo: Examinar el Modelo de contenido de los nodos mediante la vista de Modelo de contenido
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este tema se explica cómo explorar los nodos mediante la [vista Modelo de contenido](../xml-tools/content-model-view.md).

### <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>Para crear un nuevo archivo XSD y mostrar el elemento raíz en el vista Modelo de contenido

1. Cree un nuevo archivo de esquema XML.

2. Haga clic en **usar el editor XML para ver y editar el archivo de esquema XML subyacente** en la vista Inicio.

3. Copie el código de ejemplo del esquema XML del [esquema XML de ejemplo: esquema de pedido de compra](../xml-tools/sample-xsd-file-purchase-order-schema.md) y péguelo para reemplazar el código que se agregó al nuevo archivo XSD de forma predeterminada.

4. Seleccione el `purchaseOrder` elemento en el explorador de esquemas haciendo clic con el botón secundario `purchaseOrder` en el elemento en el editor XML y seleccionando **Mostrar en el explorador XML**.

5. Haga clic con el botón derecho en `purchaseOrder` dentro del Explorador XML y seleccione **Mostrar en la vista Modelo de contenido**.

     La vista Modelo de contenido muestra el elemento `purchaseOrder` en la superficie de diseño.

6. Expanda los nodos `shipTo`, `billTo` y `items` haciendo doble clic en cada nodo o haciendo clic en la flecha doble situada a la derecha de cada nodo.

     Los nodos del elemento `purchaseOrder` se expanden y puede ver el modelo de contenido del elemento.

7. Haga clic en cualquier nodo situado debajo del elemento `purchaseOrder` y busque en la barra de ruta de navegación dónde se encuentra el nodo seleccionado dentro del conjunto de esquemas.

8. Haga clic en el botón **Mostrar documentación** de la barra de herramientas XSD para alternar documentación. También puede hacer clic con el botón secundario en la superficie de diseño para ver la documentación.

9. Rick: haga clic en el `purchaseOrder` nodo y seleccione **generar XML de ejemplo** para ver el documento de instancia XML.
