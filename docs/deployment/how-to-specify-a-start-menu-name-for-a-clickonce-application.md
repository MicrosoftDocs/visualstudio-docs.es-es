---
title: 'Cómo: especificar un nombre de menú de inicio para una aplicación ClickOnce | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d6bf265b2e3761ba1fd929e72e29f4c2c47cd449
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/17/2018
ms.locfileid: "39079561"
---
# <a name="how-to-specify-a-start-menu-name-for-a-clickonce-application"></a>Cómo: especificar un nombre de menú de inicio para una aplicación ClickOnce
Cuando un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] se instala la aplicación para su uso en línea y sin conexión, se agrega una entrada para el **iniciar** menú y el **agregar o quitar programas** lista. De forma predeterminada, el nombre para mostrar es el mismo que el nombre del ensamblado de la aplicación, pero puede cambiar el nombre para mostrar estableciendo **nombre de producto** en el **opciones de publicación** cuadro de diálogo.  
  
 **Nombre de producto** se mostrará en el *publish.htm* página; para una aplicación instalada sin conexión, será el nombre de la entrada en el **iniciar** menú y, también será el nombre que se muestra en **Agregar o quitar programas**.  
  
 **Nombre del publicador** aparecerá en la *publish.htm* página anterior **nombre de producto**, y para una aplicación instalada sin conexión, también será el nombre de la carpeta que contiene la aplicación icono de la **iniciar** menú.  
  
 Puede establecer el **nombre de producto** y **nombre del publicador** propiedades en el **opciones de publicación** cuadro de diálogo, disponible en el **publicar** página de la **Diseñador de proyectos**.  
  
### <a name="to-specify-a-start-menu-name"></a>Para especificar un nombre de menú Inicio  
  
1.  Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.  
  
2.  Haga clic en el **publicar** ficha.  
  
3.  Haga clic en el **opciones** botón para abrir el **opciones de publicación** cuadro de diálogo.  
  
4.  Haga clic en **descripción**.  
  
5.  En el **opciones de publicación** diálogo cuadro, escriba el nombre para mostrar en **nombre de producto**.  
  
6.  Si lo desea, puede escribir un nombre de publicador en **nombre del publicador**.  
  
## <a name="see-also"></a>Vea también  
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Cómo: publicar una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)