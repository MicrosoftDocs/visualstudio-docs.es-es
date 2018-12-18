---
title: Integración de diseñador de esquemas XML con el Editor de XML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 43d7a8e6-bd94-4407-a800-15a145c74223
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3ae7595121fcefa36998a88b53aae466d3a726cb
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/01/2018
ms.locfileid: "34573328"
---
# <a name="integration-with-xml-editor"></a>Integración con el editor XML

El Diseñador de esquemas XML está integrado con el Editor XML. Si modifica un archivo XSD en el Editor XML, el cambio se reflejará en la [Explorador de esquemas XML](../xml-tools/xml-schema-explorer.md). Si tiene la [vista gráfico](../xml-tools/graph-view.md) o [vista modelo de contenido](../xml-tools/content-model-view.md) abierto, el cambio también se reflejará no existe. Puede navegar entre el Diseñador de esquemas XML y el Editor XML de las maneras siguientes:

-   En el Editor de XML, haga clic en un nodo y seleccione **mostrar en Explorador de esquemas XML**.

-   En la vista gráfico y la **Explorador de esquemas XML**, haga doble clic en un nodo, o haga clic en un nodo y seleccione **ver código**. En la vista de modelo de contenido, haga clic en un nodo y seleccione **ver código**.

Captura de pantalla siguiente muestra un esquema XML que se abre en el **Explorador de esquemas XML**. El **Explorador de esquemas XML** muestra el esquema especificado en una vista de árbol. El Editor XML muestra la vista de texto del nodo que está activo actualmente en el **Explorador de esquemas XML**.

![XSDDesignerWithXMLEditor](../xml-tools/media/xsddesignerwithxmleditor.gif)

A veces resulta útil ver el código en el Editor XML y en el diseñador gráfico en paralelo. Para ver ambos archivos al mismo tiempo, haga clic en cualquier lugar en el Editor XML y seleccione **Diseñador de vistas**. En el menú de Windows de Visual Studio, seleccione **nueva Horizontal (o Vertical) del grupo de pestañas**.

![XSDDesignerWithXMLEditorAndCMV](../xml-tools/media/xsddesignerwithxmleditorandcmv.gif)

## <a name="see-also"></a>Vea también

- [Explorador de esquemas XML](../xml-tools/xml-schema-explorer.md)