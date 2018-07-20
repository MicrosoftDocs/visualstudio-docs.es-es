---
title: 'Cómo: incrementar automáticamente la ClickOnce publicación de versiones | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: beada30e45ce2d46500654bca5051bd51db02d66
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/19/2018
ms.locfileid: "39151969"
---
# <a name="how-to-automatically-increment-the-clickonce-publish-version"></a>Cómo: incrementar automáticamente la ClickOnce publicación de versión
Al publicar un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación, cambiar el `Publish Version` propiedad hace que la aplicación se publica como una actualización. De forma predeterminada, Visual Studio incrementa automáticamente el `Revision` número de la `Publish Version` cada vez publique la aplicación.  
  
 Puede deshabilitar este comportamiento en el **publicar** página de la **Diseñador de proyectos**.  
  
> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-disable-automatically-incrementing-the-publish-version"></a>Para deshabilitar incrementar automáticamente la versión de publicación  
  
1.  Seleccione un proyecto en el **Explorador de soluciones**y, en el menú **Proyecto** , haga clic en **Propiedades**.  
  
2.  Haga clic en el **publicar** ficha.  
  
3.  En el **Publicar versión** sección, desactive la **incrementar revisión automáticamente con cada versión** casilla de verificación.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: establecer la publicación de ClickOnce versión](../deployment/how-to-set-the-clickonce-publish-version.md)   
 [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Cómo: publicar una aplicación ClickOnce mediante el Asistente para publicación](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)