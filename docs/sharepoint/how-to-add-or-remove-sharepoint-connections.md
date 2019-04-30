---
title: Procedimiento Agregar o quitar conexiones de SharePoint | Documentos de Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 3c094ad703727903e7109d6a748b8383e4cad7d6
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435485"
---
# <a name="how-to-add-or-remove-sharepoint-connections"></a>Procedimiento Agregar o quitar conexiones de SharePoint
  Explorador de servidores le permite examinar los sitios de SharePoint, así como las conexiones de datos. Sin embargo, para poder examinar el contenido de un sitio de SharePoint debe agregarlo a la **conexiones de SharePoint** nodo.

### <a name="to-add-a-sharepoint-site-to-the-sharepoint-connections-node"></a>Para agregar un sitio de SharePoint para el nodo Conexiones de SharePoint

1. En la barra de menús, elija **vista**, **Explorador de servidores**.

2. En **Explorador de servidores**, elija el **conexiones de SharePoint** nodo y, a continuación, en la barra de menús, elija **herramientas** > **agregar SharePoint Conexión**.

3. En el **Agregar conexión de SharePoint** , escriba el [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] para el sitio de SharePoint (por ejemplo, http://testserver/sites/unittests).

### <a name="to-delete-a-sharepoint-site-from-the-sharepoint-connections-node"></a>Para eliminar un sitio de SharePoint desde el nodo Conexiones de SharePoint

1. En la barra de menús, elija **vista**, **Explorador de servidores** para abrir **Explorador de servidores**.

2. Expanda el **conexiones de SharePoint** nodo para mostrar el sitio de SharePoint que desea eliminar de **Explorador de servidores**.

3. Elija el sitio y, a continuación, en la barra de menús, elija **editar** > **eliminar**.

    > [!NOTE]
    > Este paso no elimina el sitio subyacente. elimina solo la conexión desde **Explorador de servidores**.

## <a name="see-also"></a>Vea también
- [Examinar las conexiones de SharePoint mediante el Explorador de servidores](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)
