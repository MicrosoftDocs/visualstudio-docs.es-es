---
title: Integración con el editor XML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 43d7a8e6-bd94-4407-a800-15a145c74223
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8c0d1088e9932613466209ef8517ac5035c0b613
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656251"
---
# <a name="integration-with-xml-editor"></a>Integración con el Editor XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El Diseñador de esquemas XML está integrado con el Editor XML. Si modifica un archivo XSD en el editor XML, el cambio se reflejará en el [Explorador de esquemas XML](../xml-tools/xml-schema-explorer.md). Si tiene abierta la [vista Gráfico](../xml-tools/graph-view.md) o la [vista Modelo de contenido](../xml-tools/content-model-view.md), dicho cambio también se reflejará ahí. Puede navegar entre el Diseñador de esquemas XML y el Editor XML de las maneras siguientes:

- En el editor XML, haga clic con el botón secundario en un nodo y seleccione **Mostrar en el explorador de esquemas XML**.

- En la vista gráfico y el explorador de esquemas XML, haga doble clic en un nodo, o bien haga clic con el botón secundario en un nodo y seleccione **Ver código**. En la vista Modelo de contenido, haga clic con el botón derecho en un nodo y seleccione **Ver código**.

  En la captura de pantalla siguiente se muestra un esquema XML abierto en el Explorador de esquema XML. El Explorador de esquema XML muestra el conjunto de esquemas en una vista de árbol. El Editor XML muestra la vista de texto del nodo que está activo en el Explorador de esquema XML.

  ![XSDDesignerWithXMLEditor](../xml-tools/media/xsddesignerwithxmleditor.gif "XSDDesignerWithXMLEditor")

  A veces resulta útil ver el código en el Editor XML y en el diseñador gráfico en paralelo. Para ver ambos archivos al mismo tiempo, haga clic con el botón secundario en cualquier parte del editor XML y seleccione **Diseñador de vistas**. En el menú Ventana de Visual Studio, seleccione **Nuevo grupo de pestañas horizontal (o vertical)** .

  ![XSDDesignerWithXMLEditorAndCMV](../xml-tools/media/xsddesignerwithxmleditorandcmv.gif "XSDDesignerWithXMLEditorAndCMV")

## <a name="see-also"></a>Consulte también
 [Explorador de esquemas XML](../xml-tools/xml-schema-explorer.md)
