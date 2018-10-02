---
title: 'Cómo: incrementar automáticamente la ClickOnce publicación de versiones | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], incrementing publish version automatically
- Publish Version property, incrementing
- ClickOnce deployment, incrementing publish version automatically
- publishing, ClickOnce
ms.assetid: 686ab88a-6305-4914-a05b-fe269cc0ae1e
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: bf59ba569b7530accf4293954606923ee614d305
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47566329"
---
# <a name="how-to-automatically-increment-the-clickonce-publish-version"></a>Cómo: Incrementar automáticamente la versión de publicación de ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Cómo: incrementar automáticamente la versión de publicación de ClickOnce](https://docs.microsoft.com/visualstudio/deployment/how-to-automatically-increment-the-clickonce-publish-version).  
  
Al publicar un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicación, cambiar el `Publish Version` propiedad hace que la aplicación se publica como una actualización. De forma predeterminada, Visual Studio incrementa automáticamente el `Revision` número de la `Publish Version` cada vez publique la aplicación.  
  
 Puede deshabilitar este comportamiento en el **publicar** página de la **Diseñador de proyectos**.  
  
> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para obtener más información, consulte [Personalizar la configuración de desarrollo en Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-disable-automatically-incrementing-the-publish-version"></a>Para deshabilitar incrementar automáticamente la versión de publicación  
  
1.  Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.  
  
2.  Haga clic en el **publicar** ficha.  
  
3.  En el **Publicar versión** sección, desactive la **incrementar revisión automáticamente con cada versión** casilla de verificación.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Establecer la versión de publicación de ClickOnce](../deployment/how-to-set-the-clickonce-publish-version.md)   
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Cómo: Publicar una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)



