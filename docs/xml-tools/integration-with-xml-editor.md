---
title: Integración del Diseñador de esquemas XML con Editor XML
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 43d7a8e6-bd94-4407-a800-15a145c74223
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e06141eb6f6d7383a433a1f9b0ba29944e26a329
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55930303"
---
# <a name="integration-with-xml-editor"></a>Integración con el editor XML

El Diseñador de esquemas XML está integrado con el Editor XML. Si modifica un archivo XSD en el Editor XML, el cambio se reflejará en el [Explorador de esquemas XML](../xml-tools/xml-schema-explorer.md). Si tiene la [vista gráfico](../xml-tools/graph-view.md) o [vista modelo de contenido](../xml-tools/content-model-view.md) abierto, el cambio también se reflejará allí. Puede navegar entre el Diseñador de esquemas XML y el Editor XML de las maneras siguientes:

-   En el Editor de XML, haga clic en un nodo y seleccione **mostrar en Explorador de esquemas XML**.

-   En la vista gráfico y la **Explorador de esquemas XML**, haga doble clic en un nodo, o haga clic en un nodo y seleccione **ver código**. En la vista de modelo de contenido, haga clic en un nodo y seleccione **ver código**.

Captura de pantalla siguiente muestra un esquema de XML abierto en el **Explorador de esquemas XML**. El **Explorador de esquemas XML** muestra el esquema especificado en una vista de árbol. El Editor XML muestra la vista de texto del nodo que está activo actualmente en el **Explorador de esquemas XML**.

![XSDDesignerWithXMLEditor](../xml-tools/media/xsddesignerwithxmleditor.gif)

A veces resulta útil ver el código en el Editor XML y en el diseñador gráfico en paralelo. Para ver ambos archivos al mismo tiempo, haga doble clic en cualquier lugar en el Editor XML y seleccione **Diseñador de vistas**. En el menú de Windows de Visual Studio, seleccione **nuevo Horizontal (o Vertical) grupo de pestañas**.

![XSDDesignerWithXMLEditorAndCMV](../xml-tools/media/xsddesignerwithxmleditorandcmv.gif)

## <a name="see-also"></a>Vea también

- [Explorador de esquemas XML](../xml-tools/xml-schema-explorer.md)