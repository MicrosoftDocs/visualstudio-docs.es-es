---
title: Examen de las conexiones de SharePoint mediante el Explorador de servidores | Microsoft Docs
ms.date: 02/02/2017
ms.topic: overview
f1_keywords:
- VS.SharePointTools.SharePointExplorer.SharePointConnection
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
ms.openlocfilehash: baf580ace98ab14032de1e9a3edf18af2b2cfee8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "86016345"
---
# <a name="browse-sharepoint-connections-by-using-server-explorer"></a>Examen de las conexiones de SharePoint mediante el Explorador de servidores
  Ahora puede examinar las conexiones de SharePoint locales en el **Explorador de servidores**. Mediante esta técnica, puede navegar por los componentes de un sitio de SharePoint en el sistema. Los componentes de sitios de SharePoint, como las definiciones de lista y los tipos de contenido, aparecen en un nodo denominado **Conexiones de SharePoint** en la vista de árbol del **Explorador de servidores**. Para mostrar el **Explorador de servidores**, elija **Ver** > **Explorador de servidores** en la barra de menús. Además de mostrar los componentes de sitio de SharePoint, puede quitar elementos, ver sus propiedades o actualizar la vista de árbol mediante los comandos del menú contextual.

> [!IMPORTANT]
> Para examinar un sitio de SharePoint, debe ser administrador de la colección de sitios de SharePoint y ejecutar Visual Studio como administrador del equipo local. De lo contrario, el sitio aparece en el **Explorador de servidores**, pero no puede expandir su nodo. Para comprobar si es un administrador de la colección de sitios, abra el sitio en un explorador web, abra el menú **Acciones del sitio**, elija **Permisos del sitio** y, después, en la página **Permisos: Sitio de grupo**, elija el comando **Administradores de la colección de sitios** en el grupo **Administrar** de la cinta. Su nombre aparecerá en el cuadro de texto si es un administrador de la colección de sitios. Si el comando **Administradores de la colección de sitios** no aparece en el grupo Administrar de la cinta, significa que no es un administrador de la colección de sitios y que tiene que obtener los permisos adecuados del administrador del sitio.

## <a name="server-explorer-nodes"></a>Nodos del Explorador de servidores
 Cada componente de un sitio de SharePoint se representa mediante un nodo en la vista de árbol del **Explorador de servidores**, en **Conexiones de SharePoint**. Por ejemplo, los sitios predeterminados de SharePoint incluyen un tipo de contenido denominado Discusión, que representa un tipo de discusión que se muestra en la página **Discusiones** del sitio de SharePoint. El tipo de contenido Discusión contiene varios campos. Para ver estos campos en el **Explorador de servidores**, expanda el nodo **ContentTypes** y después el nodo **Discusión**. Contiene varios nodos de campo, como Cuerpo, Asunto de la discusión y Título.

## <a name="node-shortcut-menu-commands"></a>Comandos del menú contextual del nodo
 Cada nodo tiene un menú contextual al que se accede al hacer clic con el botón derecho en el nodo y seleccionarlo, o bien al presionar las teclas **Mayús**+**F10**. Los comandos del nodo pueden ser los siguientes:

|Nombre de comando|Descripción|
|------------------|-----------------|
|Actualizar|Actualiza la vista de árbol para reflejar cualquier cambio que se haya producido desde la última vez que se ha mostrado el nodo.|
|Eliminar|Quita el nodo seleccionado de la vista de árbol. **Nota:**  Este comando solo está habilitado en las conexiones de SharePoint que aparecen en el nodo **Conexiones de SharePoint**.|
|Propiedades|Muestra las propiedades disponibles para el nodo seleccionado en la ventana **Propiedades**. Todas las propiedades son de solo lectura y no todos los nodos tienen propiedades asociadas.|
|Agregar conexión|Permite especificar un sitio de SharePoint para examinar. Está disponible en el nodo **Conexiones de SharePoint** y en nodos de subsitio.|
|Ver en el explorador|Muestra la lista seleccionada en el explorador web. Este comando está disponible en algunas listas bajo el nodo **Listas** de **Listas y bibliotecas**.|

## <a name="related-topics"></a>Temas relacionados

|Title|Descripción|
|-----------|-----------------|
|[Cómo: para agregar o eliminar conexiones de SharePoint](../sharepoint/how-to-add-or-remove-sharepoint-connections.md)|Se describen los pasos necesarios para agregar un nuevo sitio de SharePoint al nodo **Conexiones de SharePoint** en el **Explorador de servidores**.|

## <a name="see-also"></a>Consulte también
- [Desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)
