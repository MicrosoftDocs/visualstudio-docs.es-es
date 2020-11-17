---
title: Integración del Diseñador de esquemas XML con el Editor XML
description: Obtenga información sobre la integración entre el Diseñador de esquemas XML y el editor XML y cómo se reflejan los cambios realizados en uno en el otro.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 43d7a8e6-bd94-4407-a800-15a145c74223
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9569e33f8f9f861bc5d89030c6fe38b0ab853a6f
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400192"
---
# <a name="integration-with-xml-editor"></a>Integración con el editor XML

El Diseñador de esquemas XML está integrado con el Editor XML. Si modifica un archivo XSD en el Editor XML, el cambio se reflejará en el [Explorador de esquemas XML](../xml-tools/xml-schema-explorer.md). Si tiene abierta la [vista Gráfico](../xml-tools/graph-view.md) o la [vista Modelo de contenido](../xml-tools/content-model-view.md), dicho cambio también se reflejará ahí. Puede navegar entre el Diseñador de esquemas XML y el Editor XML como se indica a continuación:

- En el Editor XML, haga clic con el botón derecho en un nodo y seleccione **Mostrar en el Explorador de esquemas XML**.

- En la vista Gráfico y en el **Explorador de esquemas XML**, haga clic en un nodo, o bien haga clic con el botón derecho en un nodo y seleccione **Ver código**. En la vista Modelo de contenido, haga clic con el botón derecho en un nodo y seleccione **Ver código**.

En la captura de pantalla siguiente se muestra un esquema XML abierto en el **Explorador de esquemas XML**. El **Explorador de esquemas XML** muestra el conjunto de esquemas en una vista de árbol. El Editor XML muestra la vista de texto del nodo que está activo en el **Explorador de esquemas XML**.

![Captura de pantalla de un proyecto de Visual Studio que muestra un nodo XML en el panel Editor XML y una vista de árbol del conjunto de esquemas en el panel Explorador de esquemas XML.](../xml-tools/media/xsddesignerwithxmleditor.gif)

A veces resulta útil ver el código en el Editor XML y en el diseñador gráfico en paralelo. Para ver ambos archivos al mismo tiempo, haga clic con el botón derecho en cualquier parte del Editor XML y seleccione **Diseñador de vistas**. En el menú Ventana de Visual Studio, seleccione **Nuevo grupo de pestañas horizontal (o vertical)** .

![Captura de pantalla de un proyecto de Visual Studio que muestra el panel Diseñador de vistas, el panel Editor XML y el panel Explorador de esquemas XML.](../xml-tools/media/xsddesignerwithxmleditorandcmv.gif)

## <a name="see-also"></a>Vea también

- [Explorador de esquemas XML](../xml-tools/xml-schema-explorer.md)
