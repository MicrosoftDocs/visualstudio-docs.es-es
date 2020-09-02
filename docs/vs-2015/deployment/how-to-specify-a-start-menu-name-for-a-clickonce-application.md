---
title: 'Cómo: especificar un nombre de menú Inicio para una aplicación ClickOnce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Start menu resource name
- Start menu name
- ClickOnce deployment, Start menu name
ms.assetid: 4b5183b2-2fd4-4433-9310-4a73bb12c4e3
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 30bb4050399bf7a6d9120f7e5454b26ce505af35
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149762"
---
# <a name="how-to-specify-a-start-menu-name-for-a-clickonce-application"></a>Cómo: Especificar un nombre en el menú Inicio para una aplicación ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cuando [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] se instala una aplicación para su uso en línea y sin conexión, se agrega una entrada al menú **Inicio** y a la lista **Agregar o quitar programas** . De forma predeterminada, el nombre para mostrar es el mismo que el nombre del ensamblado de la aplicación, pero puede cambiar el nombre para mostrar estableciendo el **nombre del producto** en el cuadro de diálogo **Opciones de publicación** .  
  
 El **nombre del producto** se mostrará en la página publish.htm; en el caso de una aplicación sin conexión instalada, será el nombre de la entrada en el menú **Inicio** y también será el nombre que se muestra en **Agregar o quitar programas**.  
  
 El **nombre del publicador** aparecerá en la página publish.htm encima del **nombre del producto**y, en el caso de una aplicación sin conexión instalada, también será el nombre de la carpeta que contiene el icono de la aplicación en el menú **Inicio** .  
  
 Puede establecer las propiedades **nombre del producto** y **nombre del publicador** en el cuadro de diálogo **Opciones de publicación** , disponible en la página **publicar** del **Diseñador de proyectos**.  
  
### <a name="to-specify-a-start-menu-name"></a>Para especificar un nombre de menú Inicio  
  
1. Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.  
  
2. Haga clic en la pestaña **Publicar**.  
  
3. Haga clic en el botón **Opciones** para abrir el cuadro de diálogo **Opciones de publicación** .  
  
4. Haga clic en **Descripción**.  
  
5. En el cuadro de diálogo **Opciones de publicación** , escriba el nombre que se mostrará en **nombre del producto**.  
  
6. Opcionalmente, puede escribir un nombre de publicador en **el nombre del publicador**.  
  
## <a name="see-also"></a>Consulte también  
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Cómo: Publicación de una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
