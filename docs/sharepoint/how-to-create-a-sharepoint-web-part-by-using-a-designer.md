---
title: 'Cómo: Crear un elemento web de SharePoint mediante un diseñador | Microsoft Docs'
titleSuffix: ''
description: Cree un elemento web agregando un elemento de elemento web visual a un proyecto de SharePoint, lo que abre el diseñador de Visual Web Developer en Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], designer
- Web Parts [SharePoint development in Visual Studio], adding
- Web Parts [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: cbbb290af0029329910a23a71f68024ee0e5e5f4
ms.sourcegitcommit: 1f27f33852112702ee35fbc0c02fba37899e4cf5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2021
ms.locfileid: "112112389"
---
# <a name="how-to-create-a-sharepoint-web-part-by-using-a-designer"></a>Cómo: Crear un elemento web de SharePoint mediante un diseñador

  Puede crear un elemento web agregando un elemento **de elemento web visual** a cualquier proyecto de SharePoint. Se abre el diseñador de Visual Web Developer en Visual Studio donde puede agregar controles y código al elemento web. Los elementos web visuales funcionan de la misma manera que lo hacen los elementos web. La única diferencia es que el usuario diseña los elementos web visuales en el diseñador de Visual Web Developer.

## <a name="to-create-a-project-for-visual-web-parts"></a>Para crear un proyecto de elementos web visuales

1. En la barra de menús, elija **Archivo** >**Nuevo** > **Proyecto**.
::: moniker range="=vs-2017"

2. En el **cuadro de diálogo** Nuevo proyecto, en Visual **C#** o **Visual Basic**, expanda el nodo **Office/SharePoint** y, a continuación, elija la **categoría Soluciones de SharePoint.**

3. En la lista de plantillas de proyecto, elija **SharePoint 2013 - Elemento web visual** y, a continuación, elija el **botón** Aceptar.

     Aparece **el Asistente para personalización de SharePoint.**
::: moniker-end
::: moniker range=">=vs-2019"
2. En el **cuadro de diálogo Crear un nuevo** proyecto, seleccione el elemento web visual de *SharePoint** para la versión concreta de SharePoint que ha instalado. Por ejemplo, si tiene instalación de SharePoint 2019, seleccione la plantilla **SharePoint 2019 - Elemento web** visual.
    [!INCLUDE[new-project-dialog-search](../sharepoint/includes/new-project-dialog-search-md.md)]

3. Cambie el nombre del proyecto si lo desea y, a continuación, elija el **botón** Crear.

::: moniker-end
4. En la página Especificar el sitio y el nivel **de** seguridad para la depuración, especifique la dirección URL de un sitio de SharePoint que se encuentra en el equipo local y, a continuación, elija **el botón** Finalizar.

     En **Explorador de soluciones**, aparece un elemento web. Después de diseñar el elemento web en el diseñador de Visual Web Developer, lo probará en el sitio que especifique.

### <a name="to-add-a-visual-web-part-to-an-existing-sharepoint-project"></a>Para agregar un elemento web visual a un proyecto de SharePoint existente

1. En la barra de menús, elija **Proyecto** >  **Agregar nuevo elemento**.

2. En el **cuadro de diálogo Agregar** nuevo elemento, elija el nodo **Office/SharePoint.**

3. En la lista de plantillas de proyecto, elija **Elemento web visual,** asígréle el nombre y, a continuación, **elija el botón** Agregar.

     En **Explorador de soluciones**, aparece el elemento web. Después de diseñar el elemento web en el diseñador de Visual Web Developer, lo probará en el sitio que especifique.

## <a name="see-also"></a>Vea también

- [Creación de elementos web para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Cómo: para crear un elemento web de SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md)
- [Tutorial: Creación de un elemento web para SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)
- [Tutorial: Creación de un elemento web para SharePoint mediante un diseñador](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)
