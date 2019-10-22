---
title: Integración del diseñador de esquemas XML con el editor XML
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 43d7a8e6-bd94-4407-a800-15a145c74223
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b9df2d97a6ff68299ab70545683970188eb1bfea
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72601784"
---
# <a name="integration-with-xml-editor"></a>Integración con el editor XML

El diseñador de esquemas XML está integrado con el editor XML. Si modifica un archivo XSD en el editor XML, el cambio se reflejará en el [Explorador de esquemas XML](../xml-tools/xml-schema-explorer.md). Si tiene abierta la [vista gráfico](../xml-tools/graph-view.md) o la [vista modelo de contenido](../xml-tools/content-model-view.md) , el cambio también se reflejará allí. Puede desplazarse entre el diseñador de esquemas XML y el editor XML de las siguientes maneras:

- En el editor XML, haga clic con el botón secundario en un nodo y seleccione **Mostrar en el explorador de esquemas XML**.

- En la vista gráfico y el **Explorador de esquemas XML**, haga doble clic en un nodo, o bien haga clic con el botón secundario en un nodo y seleccione **Ver código**. En la vista modelo de contenido, haga clic con el botón secundario en un nodo y seleccione **Ver código**.

En la captura de pantalla siguiente se muestra un esquema XML abierto en el **Explorador de esquemas XML**. El **Explorador de esquemas XML** muestra el conjunto de esquemas en una vista de árbol. El editor XML muestra la vista de texto del nodo que está actualmente activo en el **Explorador de esquemas XML**.

![XSDDesignerWithXMLEditor](../xml-tools/media/xsddesignerwithxmleditor.gif)

A veces resulta útil ver el código en el editor XML y en el diseñador gráfico en paralelo. Para ver ambos archivos al mismo tiempo, haga clic con el botón secundario en cualquier parte del editor XML y seleccione **Diseñador de vistas**. En el menú ventanas de Visual Studio, seleccione **nuevo grupo de pestañas horizontal (o vertical)** .

![XSDDesignerWithXMLEditorAndCMV](../xml-tools/media/xsddesignerwithxmleditorandcmv.gif)

## <a name="see-also"></a>Vea también

- [Explorador de esquemas XML](../xml-tools/xml-schema-explorer.md)