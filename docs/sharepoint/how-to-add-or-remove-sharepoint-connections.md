---
title: 'Cómo: agregar o quitar conexiones de SharePoint | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, browsing SharePoint sites
- SharePoint development in Visual Studio, SharePoint Connections
- SharePoint Connections [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cec1389294c8baf169db055acb87619114d7d19b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "86014563"
---
# <a name="how-to-add-or-remove-sharepoint-connections"></a>Cómo: agregar o quitar conexiones de SharePoint
  Explorador de servidores le permite examinar los sitios de SharePoint, así como las conexiones de datos. Sin embargo, antes de poder examinar el contenido de un sitio de SharePoint, debe agregarlo al nodo **conexiones de SharePoint** .

### <a name="to-add-a-sharepoint-site-to-the-sharepoint-connections-node"></a>Para agregar un sitio de SharePoint al nodo conexiones de SharePoint

1. En la barra de menús, elija **Ver**, **Explorador de servidores**.

2. En **Explorador de servidores**, elija el nodo **conexiones de SharePoint** y, a continuación, en la barra de menús, elija **herramientas**  >  **Agregar conexión de SharePoint**.

3. En el cuadro **Agregar conexión de SharePoint** , escriba [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] para el sitio de SharePoint (por ejemplo, http://testserver/sites/unittests) .

### <a name="to-delete-a-sharepoint-site-from-the-sharepoint-connections-node"></a>Para eliminar un sitio de SharePoint desde el nodo conexiones de SharePoint

1. En la barra de menús, elija **Ver**, **Explorador de servidores** para abrir **Explorador de servidores**.

2. Expanda el nodo **conexiones de SharePoint** para mostrar el sitio de SharePoint que desea eliminar de **Explorador de servidores**.

3. Elija el sitio y, a continuación, en la barra de menús, elija **Editar**  >  **eliminación**.

    > [!NOTE]
    > Este paso no elimina el sitio subyacente; solo elimina la conexión de **Explorador de servidores**.

## <a name="see-also"></a>Consulte también
- [Examinar las conexiones de SharePoint mediante Explorador de servidores](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)
