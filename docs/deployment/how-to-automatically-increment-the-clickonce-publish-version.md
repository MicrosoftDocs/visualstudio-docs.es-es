---
title: 'Cómo: automáticamente incremento el ClickOnce Publicar versión | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
ms.topic: conceptual
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
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 0a0cc134dbed973681ed43830435a6ce5ae0331c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-automatically-increment-the-clickonce-publish-version"></a>Cómo: Incrementar automáticamente la versión de publicación de ClickOnce
Al publicar un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación, cambiar el `Publish Version` propiedad hace que la aplicación se publica como una actualización. De forma predeterminada, Visual Studio incrementa automáticamente el `Revision` número de la `Publish Version` cada vez que se publica la aplicación.  
  
 Puede deshabilitar este comportamiento en el **publicar** página de la **Diseñador de proyectos**.  
  
> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-disable-automatically-incrementing-the-publish-version"></a>Para deshabilitar incrementar automáticamente la versión de publicación  
  
1.  Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.  
  
2.  Haga clic en el **publicar** ficha.  
  
3.  En el **Publicar versión** sección, desactive el **incrementar revisión automáticamente con cada versión** casilla de verificación.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Establecer la versión de publicación de ClickOnce](../deployment/how-to-set-the-clickonce-publish-version.md)   
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Cómo: Publicar una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)